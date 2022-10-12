---
layout: post
title:  "The Glyph OCR Engine"
date:   2022-04-21 11:52:19 +0300
categories: ocr
index: true
---



**Glyph** is a *work-in-progress* cloud-based **OCR engine** which was developed to provide help in digitizing scanned documents.
Currently, it supports a number of **languages** and **font types** (antiqua, fraktur / gothic and handwritten) and moderate amounts of perturbation or artifacts in the given images. Support for additional languages will be implemented in the future.

Glyph is intended to be used mainly via its **API** (detailed below) and be embedded into projects or scripts without introducing external modules or large code snippets. Therefore, it is currently not targeted for end-users.

<div class="slideshow-container">
  <div class="slide fade">
    <img src="/assets/img/index_sections/text_recognition/de-frk-demo.png">
  </div>

  <div class="slide fade">
    <img src="/assets/img/index_sections/text_recognition/ua-hw-demo.png">
  </div>

  <div class="slide fade">
    <img src="/assets/img/index_sections/text_recognition/en-ma-demo.png">
  </div>

  <div class="slide fade">
    <img src="/assets/img/index_sections/text_recognition/fr-ma-demo.png">
  </div>

  <div class="slide fade">
    <img src="/assets/img/index_sections/text_recognition/ua-hw-demo2.png">
  </div>

  <div class="slide fade">
    <img src="/assets/img/index_sections/text_recognition/ro-ma-demo.png">
  </div>

  <div class="slide fade">
    <img src="/assets/img/index_sections/text_recognition/de-ma-demo.png">
  </div>

  <span class="prev" onclick="plusSlides(-1)">&#10094;</span>
  <span class="next" onclick="plusSlides(1)">&#10095;</span>
</div>


## Supported Languages

At the time of writing, Glyph can handle the following pairs of languages and script types:

- **English - Antiqua** (lang code: `en-ma`)
- **French - Antiqua** (lang code: `fr-ma`)
- **German - Fraktur / Gothic** (lang code: `de-frk`)
- **German - Antiqua** (lang code: `de-ma`)
- **Romanian - Antiqua** (lang code: `ro-ma`)
- **Romanian - Handwritten (old)** (lang code: `ro-ma`)
- **Ukrainian - Handwritten (old)** (lang code: `ua-hw`)

Benchmarking is performed for each available pair and the performances are compared to existing products; see more details about [Glyph's Benchmarks](/ocr/comparison-of-ocr-engines).


## API Requests

Glyph is exposed as a **web service** over HTTPS at the address `https://glyph.api.overfitted.io/process`.
When interacting with Glyph, a **POST**-type **request** must be crafted and directed to the aforementioned address. Glyph accepts the following **arguments** inside the request:

* `img`: the image you're submitting for text recognition
* `lang`: the language and font type (script) of your submitted image; supported values are:
    * `en-ma`: English / Antiqua
    * `fr-ma`: French / Antiqua
    * `de-frk`: German / Fraktur (Gothic)
    * `de-ma`: German / Antiqua 
    * `ro-ma`: Romanian / Antiqua
    * `ua-hw`: Ukrainian / Handwritten
* `words_only` (optional; default: `false`): instructs the Glyph engine to treat each word as a line of text, which might prove useful in identifying texts from non-uniform inputs such as receipts; to enable, set this parameter to `true`
* `api_key`: this is your API key which uniquely identifies your account; see the [Getting Started](/get-started) section for more information on this


## API Responses

Glyph will issue **JSON**-strucutred **responses** to each request in a synchronous manner.

> **Note:** in the event of a server overload, an **Internal Server Error(500)** will be returned; please check the **error code** returned by Glyph and recreate the POST request if necessary. 

A successful response from Glyph includes the following fields:
* `text`: the entire recognized text as a multiline string (`\n` as separator)
* `lines`: a list which presents information at line level; contains elements with the following structure:
    * `x0`, `y0`, `x1`, `y1`: denote the bounding rectangle coordinates for the current text line
    * `confidence`: a value which indicates how confident is Glyph that the line is of interest and not an artifact or noise
    * `line`: a list which presents character-level information from the recognition process:
        * `x0`, `y0`, `x1`, `y1`: represent the bounding rectangle coordinates for each identified character
        * `character`: contains the identified character (unicode supported)
        * `confidence`: the confidence of Glyph for the current character recognition

## Example

A short Python example is provided for easier understanding [![Glyph on Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Ld9f0I_Wl74EH16fUVneKmIavPept5C8?usp=sharing){:class='no-icon'}{:target="_blank"}.

However, you'll still need to supply your own **API key** before running it.
Alternatively, you'll find below a JSON response from Glyph for a single image containing only the word *"Alle"*.
```json
{
    "text": "Alle",
    "lines": [
        {
            "x0": 17,
            "y0": 9,
            "x1": 837,
            "y1": 54,
            "confidence": 0.8112224489450455,
            "line": [
                {
                    "character": "A",
                    "confidence": 0.7507894039154053,
                    "x0": 74,
                    "x1": 82,
                    "y0": 9,
                    "y1": 54
                },
                {
                    "character": "l",
                    "confidence": 0.9985935091972351,
                    "x0": 119,
                    "x1": 123,
                    "y0": 9,
                    "y1": 54
                },
                {
                    "character": "l",
                    "confidence": 0.9996170997619629,
                    "x0": 130,
                    "x1": 134,
                    "y0": 9,
                    "y1": 54
                },
                {
                    "character": "e",
                    "confidence": 0.999936580657959,
                    "x0": 145,
                    "x1": 149,
                    "y0": 9,
                    "y1": 54
                }
            ]
        }
    ]
}
```