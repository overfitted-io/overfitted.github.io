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

Glyph can currently handle the following pairs of **languages** and **scripts**:

- **English - Antiqua** (lang code: `en-ma`)
- **French - Antiqua** (lang code: `fr-ma`)
- **German - Fraktur / Gothic** (lang code: `de-frk`)
- **German - Antiqua** (lang code: `de-ma`)
- **Romanian - Antiqua** (lang code: `ro-ma`)
- **Romanian - Handwritten** (lang code: `ro-hw`)
- **Ukrainian - Handwritten (old documents)** (lang code: `ua-hw`)

At the time of writing, we prioritize languages which are actively requested by customers; please [contact us](/contact) if you need a specific language to be added. 

## Capabilities

* **Non-Uniform Pages**: it can handle pages in which the font size varies between text rows
* **White Text / Black Background**: it supports lighter texts on darker backgrounds (still being tested)
* **Moderate Noise / Artifacts**: it can handle documents with moderate amounts of degradation or skew


## Technical Advantages

Integrating Glyph into suitable projects can provide a series of advantages:
1. **No Hardware Requirements:** since all the CPU/GPU/RAM intensive operations take place on our cloud infrastructure, your project will not be constrained by additional hardware requirements
2. **Minimal Footprint:** by default, Glyph does not require any particular resources, modules or libraries to be embedded into your project as long as a POST internet request can be made
3. **Flexibility:** as a cloud-based OCR/HTR engine, Glyph is language-agnostic and therefore will not impose a specific programming language when being queried
4. **Always @Latest Version:** because all requests are centralized on our platform, all users will benefit from the latest version of Glyph without needing to perform further local actions
5. **Developer Friendly:** by having all of Glyph's responses as JSON-formatted strings, one can easily parse and analyze the results


## API Requests

**HTTPS Endpoint**: `https://glyph.api.overfitted.io/process`

When interacting with Glyph, a **POST**-type **request** with `multipart/form-data` encoding must be submitted to the aforementioned endpoint. The information transmitted to the OCR engine will be structured using a set of predefined field names; see below for details.

Alternatively, if you're developing in Python3, you can install the [Python3 API Client](https://github.com/overfitted-io/python-api-client) and use the built-in functions to create these requests.

### Request Format
* `img` [**Bytes**, required]: the **image** you're submitting for text recognition
* `lang` [**String**, required]: the **language** and **script** of your submitted image - see the *lang codes* from [supported languages](#supported-languages) for possible values
* `api_key` [**String**, required]: this is your **API key** which uniquely identifies your account; see the [Getting Started](/get-started) section for more information on this


## API Responses

Glyph will issue a **JSON**-structured **response** to each request in a **synchronous** manner. It is recommended to always check the HTTP **status code** returned by the OCR engine before parsing the JSON response since these responses differ in structure when errors occur.

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

For brevity, a one-word image was submitted for processing; the response is attached below:

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