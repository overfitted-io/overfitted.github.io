---
layout: post
title:  "Glyph API Documentation"
date:   2022-04-21 11:52:19 +0300
categories: glyph
index: true
---

This document includes the available documentation for interacting with the **Glyph** text recognition engine through its API.

## Endpoint
```
https://glyph.api.overfitted.io/process
```


## Parameters
In POST-type requests, the following parameters are available:
* `img`: the image you're submitting for text recognition
* `lang`: the language and font type (script) of your submitted image; supported values are:
    * `de-ma`: German / Antiqua 
    * `de-frk`: German / Fraktur (Gothic)
    * `ua-hw`: Ukrainian / Handwritten
* `uniform_img` (optional; default: `false`): instructs the Glyph engine to treat the input as an uniform text image - i.e.: structured lines of text without artifacts or non-text elements nearby; to enable, set this parameter to `true`
* `api_key`: this is your API key which uniquely identifies your account; see the [Getting Started](/get-started) section for more information on this



For example, the following **curl** command submits **my_image.tiff** using **de-frk** as language code. 
```bash
curl -H "Content-Type: multipart/form-data" \
     -F "lang=de-frk" \
     -F "api_key=<your_api_key>" \
     -F "img=@my_image.tiff" \
     https://glyph.api.overfitted.io/process
```

## Response

Glyph responds with a **JSON**-formatted output which includes the following fields:
* `text`: the entire recognized text as a multiline string (`\n` as separator)
* `lines`: a list which presents information at line level; contains elements with the following strucutre:
    * `x0`, `y0`, `x1`, `y1`: denote the bounding rectangle coordinates for the current text line
    * `script` : the guessed type of script used to write the line (possible values: `ANTIQUA`, `FRAKTUR`, `HANDWRITTEN`)
    * `confidence`: a value which indicates how confident is Glyph that the line is of interest and not an artifact or noise
    * `line`: a list which presents character-level information from the recognition process:
        * `x0`, `y0`, `x1`, `y1`: represent the bounding rectangle coordinates for each identified character
        * `character`: contains the identified character (unicode supported)
        * `confidence`: the confidence of Glyph for the current character recognition 

Below is an example of Glyph's response for the task of recognizing, for brevity, a single word from a given image.
```json
{
    "text": "Alle",
    "lines": [
        {
            "x0": 17,
            "y0": 9,
            "x1": 837,
            "y1": 54,
            "script": "FRAKTUR",
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