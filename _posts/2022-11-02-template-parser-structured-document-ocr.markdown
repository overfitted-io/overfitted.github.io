---
layout: post
title:  "Template Parser for Structured Document OCR"
date:   2022-11-02 11:52:19 +0300
categories: template-parser
index: true
---

## About

The **Template Parser** is a cloud-hosted service which performs *sensible* yet robust **OCR** by paying attention to **semantics** introduced by the **text's location**. For example, certain fixed-structure forms or documents place specific information (*names, dates, addresses, numeric identifiers, etc.*) in the same region each time. This information may or may not be explicitly annotated and its true meaning is inferred from the location within the document. 

This service is designed to handle tasks in which a **template** of the document is provided and **text locations** are known for that template. It will attempt to map the **text locations** from the **template** to the **targeted document** and compensate for alignment errors, cropping, skew and different perspectives. Under the hood, it relies on [Glyph](/ocr/glyph-ocr-engine) for text recognition, which means it can be extended to recognize even **handwriting**.

It can be accessed either through the [Python3 API Client](https://github.com/overfitted-io/python-api-client) or by crafting direct requests which follow the [standards](#api-requests).

A small example is attached below which illustrates how **Template Parser** handles the text extraction from a **Romanian Identity (ID) Card** (specimen) with artificially introduced background noise. More details with regard to this project and examples can be found [here](/template-parser/text-extraction-romanian-id-cards-ocr).

{% include image.html
            description="Using the **Template Parser** to recognize text from specific fields of a **Romanian ID Card**"
            size="60%"
            url="/assets/img/posts/template-parser-structured-document-ocr/template-parser-demo.png" %}

## Required Information

The following information needs to be supplied especially for this service:
* **template image:** this represents the image that will be used for context; ideally, this image has minimal perturbation and has an orthogonal view
* **target image:** the image of interst, which contains the text that needs to be recognized
* **text locations:** often called *Regions of Interest* (**ROI**s), which specify, in the template image, where each field is to be found; uses pixels as metric

As an example, in the following **template image** the highlighted **ROI** specifies where the **Last Name** is found; the rectangle is defined through the upper-left and lower-right points.

{% include image.html
            description="In this template image we say that the **Last Name** can be found in the rectangle `(306, 194, 700, 229)`; note that the **ROI** must be large enough to cover possibly longer texts"
            size="40%"
            url="/assets/img/posts/template-parser-structured-document-ocr/template-image-example.png" %}

## API Requests

**HTTPS Endpoint**: `https://template-parser.api.overfitted.io/process`

A **POST**-type **request** with `multipart/form-data` encoding must be submitted to the Template Parser through its public endpoint. 

### Request Format

* `img` [**Bytes**, required]: this is the **target image** or the image of interest
* `template_img` [**Bytes**, required]: is the **template image** used to acquire context
* `lang` [**String**, required]: defines what **language** and **script** to use for the OCR engine
* `rois` [**Array[Int]**, required]: is the list of **ROI**s or fields of interest; its lenght must be **divisible by 4** 
* `api_key` [**String**, required]: your account's **API key**; see [Getting Started](/getting-started) for more details

## API Responses

This service generates a **JSON**-formatted **synchronous** response. In case of an error, the **status code** will be different than **200** and details will be provided in the actual response.

### Successful Response Fields

* `match_score`: represents how well the template can be mapped to the targeted image 
* `fields`: is a 'dictionary' which contains multiple ROIs in the *same order* as in the request
  * `roi<N>`: includes information for the *Nth* ROI
    * `coords`: 
      * `p1`, `p2`, `p3`, `p4`: these are 4 points in `(X,Y)` format which indicate the location of the ROI in the target image 
      * `content`: is the OCR engine's response for this specific ROI; see details in [Glyph's Documentation](/ocr/glyph-ocr-engine#successful-response-fields) 

### Example of a Successful Response

This is a response returned by the Template Parser for a single **ROI** in which the **text** `TM` was discovered.

```JSON
{
  'match_score': 0.16795580110497238, 
  'fields': 
  {
    'roi1': 
    {
      'coords': {
        'p1': [572, 111], 
        'p2': [623, 110], 
        'p3': [622, 139], 
        'p4': [571, 140]}, 
        'content': 
        {
          'text': 'TM', 
          'angle': -1, 
          'lines': 
          [
            {
              'x0': 0, 
              'y0': 0, 
              'x1': 49, 
              'y1': 28, 
              'confidence': 1, 
              'line': 
              [
                {'character': 'T', 'confidence': 0.9366891980171204, 'x0': 13, 'x1': 16}, 
                {'character': 'M', 'confidence': 0.9081507921218872, 'x0': 25, 'x1': 27}
              ]
            }
          ]
        }
      }
  }
}
```