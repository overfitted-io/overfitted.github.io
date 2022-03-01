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
data = {'lang' : 'en-ma'}
files = {'img': open('some-image.png', 'rb')}

response = requests.post('https://glyph-main.api.overfitted.io/process', files=files, data = data)

print(response.text)
```



## Supported Languages
- English - Modern Antiqua (lang code: *en-ma*) (25.02.2022) ([see benchmark](/benchmarks/ocr/glyph-en-modern-antiqua-benchmark))
- German - Modern Antiqua (lang code: *de-ma*) (01.03.2022) ([see benchmark](/benchmarks/ocr/glyph-de-modern-antiqua-benchmark))

## Supported Layouts
- One-column text (25.02.2022)