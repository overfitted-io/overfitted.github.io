---
layout: section-tab
icon: /assets/img/icons/ocr.svg
title: Optical Character Recognition
---

The **Glyph Engine** (work in progress) is an *Optical Character Recognition* (**OCR**) system which supports text segmentation and recognition for multiple languages, given colorized, grayscaled or binarized documents.


## API
Currently, interaction with the **Glyph API** can be made using **POST** requests.
For example, a Python implementation of such request is provided below.
```python
import requests

# see lang codes below
data = {'lang' : 'de-frk'}
files = {'img': open('glyph_demo1.png', 'rb')}

# submit a POST request to Glyph's endpoint
response = requests.post('https://glyph.api.overfitted.io/process', files=files, data = data)

# NOTE: do check the response's status_code
if response.status_code == 200:
    print('Found text:', response.text)
```




## Supported Languages
- **German** - Fraktur (lang code: *de-frk*) (03.03.2022) ([see benchmark](/benchmarks/ocr/glyph-de-fraktur-benchmark))

## Supported Layouts
- One-column text (25.02.2022)