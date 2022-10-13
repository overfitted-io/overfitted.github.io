---
layout: section-tab
title: Document Template Parser
color: fff6eb
---

## Template Parser
{:class="left-border-header" style="font-size: 30px"}

Parses fixed-format images (*e.g., documents, forms*) and extracts the text from various **fields of interest** (*e.g., names, dates*) by relying on a known (provided) **template** and the defined **regions of interest** to identify positions of relevant information within the targeted document.

Results are returned in **textual** (OCR-ed) format.

> **Note:** the JSON result has been formatted to be more intuitive for this use case; please refer to the documentation for a more accurate representation of the service's response.

<div style="background-color: #fff; text-align: center; overflow:auto;">
<img src="{{ '/assets/img/index_sections/template_parser/w2_highlight.png' | relative_url }}" style="display: inline-block; pointer-events: none; user-select: none; min-width: 200px; max-width:50%;">
<pre style="display: inline-block; vertical-align: middle; background-color: transparent; border: none; text-align: left;">
{
    <span style="font-weight: bold">"EMPLOYEE_SSN":</span> <span style="color: orangered">"123-45-6789<strong>.</strong>"</span>, 
    <span style="font-weight: bold">"EMPLOYER_IN":</span> <span style="color: orangered">"11-2233445"</span>, 
    <span style="font-weight: bold">"EMPLOYER_NAME":</span> <span style="color: orangered">"The Big Company \
                    1<strong>8</strong>3 Main Street \
                    Anywhere, PA 12345"</span>, 
    <span style="font-weight: bold">"EMPLOYEE_NAME":</span> <span style="color: orangered">"Jane A<strong>.</strong> D<strong>Q</strong>E \
                    123 Elm Street \
                    Anywhere Else, PA 23456"</span>
}
</pre>
</div>





