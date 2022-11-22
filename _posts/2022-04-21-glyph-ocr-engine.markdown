---
layout: post
title:  "The Glyph OCR Engine"
date:   2022-04-21 11:52:19 +0300
categories: ocr
index: true
---


## About
**Glyph** is a cloud-based **OCR / HTR** engine which was developed internally to aid in extracting texts from scanned or photographed documents. It supports multiple combinations of **languages** and **scripts** and can be employed in recognizing various formats, ranging from the old **fraktur / gothic** fonts to **modern characters** and even **handwriting**.

Glyph is designed to provide a verbose **feedback** for each text recognition task by including *bounding boxes* (at multiple levels), *confidence values*, *angles* and other relevant features which help improving **explainability** and **verifying the correctness** of each result. 

It is integrated into the [ScreenOCR](/ocr/screenocr-fast-ocr-windows-keyboard-shortcut) Windows Application for quick access and testing. Programatically, Glyph can be queried through its **API** using either our [Python3 API Client](https://github.com/overfitted-io/python-api-client) or by creating web requests according to our [documentation](#api-requests).


<div class="slideshow-container">
  <div class="slide slide-medium fade">
    <img src="/assets/img/index_sections/text_recognition/de-frk.png">
  </div>

  <div class="slide slide-medium fade">
    <img src="/assets/img/index_sections/text_recognition/ro-hw.png">
  </div>

  <div class="slide slide-medium fade">
    <img src="/assets/img/index_sections/text_recognition/en-ma.png">
  </div>

  <div class="slide slide-medium fade">
    <img src="/assets/img/index_sections/text_recognition/fr-ma.png">
  </div>

  <div class="slide slide-medium fade">
    <img src="/assets/img/index_sections/text_recognition/ro-ma.png">
  </div>

  <span class="prev" onclick="plusSlides(-1)">&#10094;</span>
  <span class="next" onclick="plusSlides(1)">&#10095;</span>
</div>

## Supported Languages

At the time of writing, Glyph can handle the following pairs of **languages** and **scripts**:

- **English - Antiqua** (lang code: `en-ma`)
- **French - Antiqua** (lang code: `fr-ma`)
- **German - Fraktur / Gothic** (lang code: `de-frk`)
- **German - Antiqua** (lang code: `de-ma`)
- **Romanian - Antiqua** (lang code: `ro-ma`)
- **Romanian - Handwritten** (lang code: `ro-hw`)
- **Ukrainian - Handwritten (old documents)** (lang code: `ua-hw`)

At the time of writing, we prioritize languages which are actively requested by customers; please [contact us](/contact) if you need a specific language to be integrated in Glyph. 

## Technical Advantages

Integrating Glyph into suitable projects can provide a series of advantages:
1. **No Hardware Requirements:** since all the CPU/GPU/RAM intensive operations take place on our cloud infrastructure, your project will not be constrained by additional hardware requirements
2. **Minimal Footprint:** by default, Glyph does not require any particular resources, modules or libraries to be embedded into your project as long as a POST internet request can be made
3. **Flexibility:** as a cloud-based OCR/HTR engine, Glyph is language-agnostic and therefore will not impose a specific programming language when being queried
4. **Always @Latest Version:** because all requests are centralized on our platform, all users will benefit from the latest updates as soon as they're applied without needing to perform further actions
5. **Programmer Friendly:** since all of Glyph's responses are presented as a JSON-formatted string which can be easily parsed and analyzed

## Pricing

Glyph implements a **granular pricing** scheme in which **platform credits** are consumed according to the **number of recognized characters**. This means images with small amounts of text will consume fewer credits than, e.g., a page from a book. 

At the time of writing, Glyph charges **0.01 credits** per **1000 characters**, with character-level granularity.

## API Requests

Glyph's endpoint is exposed at the following address: `https://glyph.api.overfitted.io/process`.
When interacting with Glyph, a **POST**-type **request** must be crafted and directed to the aforementioned address.

### Possible Request Arguments
* `img` (Bytes): the image you're submitting for text recognition
* `lang` (String): the language and font type (script) of your submitted image - see the lang codes from [supported languages](#supported-languages).
* `words_only` (String) (optional; default: `false`): instructs the Glyph engine to treat each word as a line of text, which might prove useful in identifying texts from non-uniform inputs such as receipts; to enable, set this parameter to `true`
* `api_key` (String): this is your API key which uniquely identifies your account; see the [Getting Started](/get-started) section for more information on this


## API Responses

Glyph will issue a **JSON**-structured **response** to each request in a **synchronous** manner. It is recommended to always check the HTTP status code returned by the OCR engine before parsing the JSON response since these responses differ in structure when errors occur.

### Successful Response Fields
* `text`: the entire recognized text as a multiline string (`\n` as separator)
* `angle`: the skew angle detected for the identified image
* `lines`: a list which presents information at line level; contains elements with the following structure:
    * `x0`, `y0`, `x1`, `y1`: denote the bounding rectangle coordinates for the current text line
    * `confidence`: a value which indicates how confident is Glyph that the line is of interest and not an artifact or noise
    * `line`: a list which presents character-level information from the recognition process:
        * `x0`, `x1`: represent the horizontal bounds for each identified character
        * `character`: contains the identified character (unicode supported)
        * `confidence`: the confidence of Glyph for the current character recognition

### Example of a Successful Response

```json
{
    "text": "Alle",
    "angle": 0,
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
                },
                {
                    "character": "l",
                    "confidence": 0.9985935091972351,
                    "x0": 119,
                    "x1": 123,
                },
                {
                    "character": "l",
                    "confidence": 0.9996170997619629,
                    "x0": 130,
                    "x1": 134,
                },
                {
                    "character": "e",
                    "confidence": 0.999936580657959,
                    "x0": 145,
                    "x1": 149,
                }
            ]
        }
    ]
}
```