---
layout: post
title:  "Robust Text Extraction from Romanian ID Cards through OCR"
date:   2022-11-03 11:52:19 +0300
categories: template-parser
index: true
---


This short demo approaches the problem of extracting fields of interest, in textual format, from images that contain documents with a fixed structure. In this scenario, the meaning of certain fields is determined by their location within the document therefore requiring knowledge with regard to the used template.

The documents presented here are **Romanian Identity (ID) Cards** discovered by our crawler, which match the following ethical criteria:
- all shown documents are expired at the time of writing and therefore unusable
- all critical fields which remain unchanged in newer versions of these documents, e.g., *Personal Identification Number* (**ro:** *Cod Numeric Personal* - abbr.: *CNP*), are blurred in postprocessing
- all portrait photos and location addresses are blurred in postprocessing to prevent doxing
- revealed unique identifiers such as *Series* (**ro:** *Serie*) or *Number* (**ro:** *Nr.*) are known to be updated once a new ID card is issued for the same person and therefore hold no further value

The template document is an exception to this rule and therefore includes all available information because it is classified as a sample card (**ro:** *specimen*) and publicly exposed on [OECD's Official Website](https://www.oecd.org/tax/automatic-exchange/crs-implementation-and-assistance/tax-identification-numbers/Romania-TIN.pdf)

## Challenges

Typically, ID card scanning is performed in a controlled and ideal environment where the following favorable assumptions hold:
- the documents are placed in **similar locations** each time
- the camera captures **orthogonal views** of the documents 
- the background presents little to **no amounts of noise**
- the documents are **not skewed** or present minimal skew and have **similar sizes**
- many **camera parameters remain fixed** (e.g., lens characteristics, brightness, zoom, contrast)
- many **environment parameters remain fixed** (e.g., lightning)

These assumptions **do not hold** for this demo.

In this demo, images originate from different smartphone cameras and tend to invalidate most of the aforementioned assumptions therefore imposing additional challenges for the text extraction process. The results presented here, while underlining the robustness of the method, can be improved if the process is performed in ideal environments.

## Implementation

The demo relies on the **Template-Parser** service exposed in the platform and the official Python3 **API client** to achieve fast results without reimplementing large portions of code.
In general, the approach relies on providing the following information:
1. a **template image** - an image which contains the isolated document with minimal perturbations
2. a **target image** - the image which undergoes the text extraction / OCR process
3. the **coordinates** of specific **fields** within the **template image** - these will be mapped on the target image

Under the hood, the service will attempt to locate the given coordinates in the **target image** and extract the texts found at the indicated locations.



### Requirements

Start by installing the Python3 based [API client](https://github.com/overfitted-io/python-api-client) to facilitate easier interactions with the **Template-Parser**. To do so, run the following command in your terminal:
```bash
pip3 install git+https://github.com/overfitted-io/python-api-client.git
```

Also, ensure that you have an active **API key**; if not, check the [Get Started](https://overfitted.io/get-started/) section to get one.

The API key must be placed in the `OVERFITTED_IO_API_KEY` environment variable as follows:
```bash
# TODO: replace with your key
export OVERFITTED_IO_API_KEY=123456789abcdef
```

### Defining Regions of Interest

A *Region of Interest* (**ROI**) is a rectangle within the **template image** which marks the boundaries of a field. The rectangle is defined by its **upper-left** and **lower-right** corners in the format `(x1, y1, x2, y2)`. The coordinates of the rectangle represent the number of pixels from the origin `(0, 0)`, which is conventionally considered being the **upper-left** corner of the image.

The rectangles which represent **ROI**s are mapped from the **template image** to the **target image** in order to retrieve textual content while also accounting for location-based semantics.

In the example below, the coordinates for the `LAST_NAME` field are shown; the same process is repeated for each **ROI**, resulting in a list of such regions.


{% include image.html
            description="In this template image we say that the `LAST_NAME` can be found in the rectangle `(306, 194, 700, 229)`; note that the **ROI** must be large enough to cover possibly longer texts"
            size="60%"
            url="/assets/img/posts/text-extraction-romanian-id-cards-ocr/template-demo.png" %}


### Querying the Service

A fairly simple script creates a single request to the **Template-Parser** through the `query_service()` method, which is exposed by the previously installed API client. 

The request must include:
- 2 images (**template image** & **target image**)
- a **language** hint for the OCR engine; `ro-ma` (*Romanian Modern Antiqua*) is used in this demo given the documents are in Romanian
- a **list of ROIs**, which is the concatenation of all defined **ROI**s of length **4xN** for **N** **ROIs** with **4** coordinates each
- an **API key**
- **optional:** a parameter which instructs the OCR engine to treat each **ROI** as a **single line** of text.

The first version of this script could be implemented as follows.
```python
import overfitted_io_client as oc

# ROIs from the template image 
ROU_ID_ROIS = {
    'SERIES' : [583, 115, 632, 143],
    'NUMBER' : [669, 115, 791, 143], 
    'LAST_NAME' : [306, 194, 700, 229],
    'FIRST_NAME' : [306, 246, 700, 278],
    'NATIONALITY' : [306, 296, 600, 325],
    'ISSUED_BY' : [306, 490, 600, 522],
    'VALIDITY' : [670, 485, 1015, 530]
}

# reads target image (img) and template image (template) from disk
with open('target.jpg', 'rb') as img, open('template.jpg', 'rb') as template:

    # query the template parser
    response = oc.query_service(
        service = 'template-parser', 
        inputs = [
                    { 
                        'img' : img, # target image
                        'template_img' : template,  # template image
                        'lang' : 'ro-ma',  # OCR language hint; using Romanian Modern Antiqua in this case
                        'api_key' : oc.config.get_api_key(), # this gets the API key from the environment variable
                        'rois' : ROU_ID_ROIS['SERIES'] + # concatenate all the ROIs coordinates into a single list
                                    ROU_ID_ROIS['NUMBER'] + 
                                    ROU_ID_ROIS['LAST_NAME'] + 
                                    ROU_ID_ROIS['FIRST_NAME'] + 
                                    ROU_ID_ROIS['NATIONALITY'] + 
                                    ROU_ID_ROIS['ISSUED_BY'] + 
                                    ROU_ID_ROIS['VALIDITY'],
                        'skip_seg' : 'true' # all fields seem to be single-lined, so we instruct the OCR engine to bypass the segmentation step
                    }
                ])
                
    # assuming one image is sent, the list of responses has only 1 item
    # the format is discussed below
    result, status = response[0]
    print(result)
```

### Understanding the Response

The response is **JSON**-formatted; for brevity, only the more important parts of the response are discussed here.

A valid response includes the following attributes:
- `match_score`: indicates how much the template resembles the target image
- `fields`: is a 'dictionary' which contains multiple ROIs in the *same order* as in the request
    - `roi<N>`: includes information for the *Nth* ROI
        - `coords`: contains 4 points in `(X,Y)` format which indicate the location of the ROI in the target image
        - `content`: contains various information from the **OCR** engine 
            - `text`: contains the concatenated **text** found for the current ROI

For example, a truncated response is presented; it corresponds to a ROI which contains the text *"TM"*.
```json
{
    "match_score": 0.16795580110497238,
    "fields": {
        "roi1": {
            "coords": {
                "p1": [ 572, 111 ],
                "p2": [ 623, 110 ],
                "p3": [ 622, 139 ],
                "p4": [ 571, 140 ]
            },
            "content": {
                "text": "TM",
                [ ... ]
            }
        }
    }
}
```

### Repository & Qualitative Results

The script used to generate the images in this section is an augmented version of the one previously presented. It additionally parses the response and draws bounding polygons around the identified ROIs, as well as inserting the recognized texts in the image. 

It is available as a [GitHub Repository](https://github.com/overfitted-io/demo-romanian-id-card-ocr).

The original images couldn't be included unless they were heavily blurred which would mitigate some of the performance of this service; therefore, two publicly available samples are used instead with artificially introduced background noise.

<div class="slideshow-container">
  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/1.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/2.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/3.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/4.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/5.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/6.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/7.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/8.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/9.png">
  </div>

  <div class="slide slide-large fade">
    <img src="/assets/img/posts/text-extraction-romanian-id-cards-ocr/slideshow/10.png">
  </div>

  <span class="prev" onclick="plusSlides(-1)">&#10094;</span>
  <span class="next" onclick="plusSlides(1)">&#10095;</span>
</div>

### Notes and Further Assistance

Although the results seem promising, some errors might still occur. It is highly recommended to not rely entirely on the accuracy of this approach and implement additional validation methods. Some examples include text-level checks such as:
- character-level **text correction** based on a known **vocabulary** of words
- RegEx-based **format validation** (e.g., a field should be numbers-only or should match a specific format)
- **fuzzy searching** using multiple fields (i.e., if one field is not correctly recognized, others can compensate for the error)

Should you have questions, feel free to reach out for further assistance with regard to this topic.















