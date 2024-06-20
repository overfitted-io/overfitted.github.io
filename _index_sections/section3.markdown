---
layout: section-tab
title: Document Parser
color: fff6eb
---

## Doc Parser
{:class="left-border-header" style="font-size: 30px"}

Parses fixed-format images (*e.g., documents, forms*) and extracts the text from various **fields of interest** (*e.g., names, dates, numeric IDs, etc.*) by relying on a known (provided) **template** and the defined **regions of interest** to identify positions of relevant information within the targeted document.


<div style="background-color: #fff; text-align: center; overflow:auto;">
<img src="{{ '/assets/img/index_sections/template_parser/romanian_id_card_model.png' | relative_url }}" style="display: inline-block; pointer-events: none; user-select: none; min-width: 200px; max-width:60%;">
<pre style="display: inline-block; vertical-align: middle; background-color: transparent; border: none; text-align: left;">
{
    <span style="font-weight: bold">"match_score":</span> 0.5011664535634441,
    <span style="font-weight: bold">"last_name_field":</span> <span style="color:#FFE97F">"VASILESCU"</span>,
    <span style="font-weight: bold">"first_name_field":</span> <span style="color:#FF7F7F">"ELENA"</span>,
    <span style="font-weight: bold">"cnp_field":</span> <span style="color:#FF6A00">"2410415400342"</span>,
    
    <span style="font-weight: bold">"MRZ":</span> 
    {
        <span style="font-weight: bold">"doctype":</span> <span style="color:#FFD800">"ID"</span>,
        <span style="font-weight: bold">"country":</span> <span style="color:#FF7F7F">"ROU"</span>,
        <span style="font-weight: bold">"last_name":</span> <span style="color:#4CFF00">"VASILESCU"</span>,
        <span style="font-weight: bold">"first_name":</span> <span style="color:#0094FF">"ELENA"</span>,
        <span style="font-weight: bold">"series":</span> <span style="color:#FF00DC">"SS"</span>,
        <span style="font-weight: bold">"number":</span> <span style="color:#00FFFF">"099994"</span>,
        <span style="font-weight: bold">"nationality":</span> <span style="color:#FF6A00">"ROU"</span>,
        <span style="font-weight: bold">"birthday":</span> <span style="color:#FF7F7F">"410415"</span>,
        <span style="font-weight: bold">"sex":</span> <span style="color:#00FFFF">"F"</span>,
        <span style="font-weight: bold">"validity":</span> <span style="color:#FFE97F">"770415"</span>,
        <span style="font-weight: bold">"cnp_first_digit":</span> <span style="color:#FF006E">"2"</span>,
        <span style="font-weight: bold">"cnp_suffix":</span> <span style="color:#4800FF">"400342"</span>,
        <span style="font-weight: bold">"series_number_crc_match":</span> 0,
        <span style="font-weight: bold">"birthday_crc_match":</span> 0,
        <span style="font-weight: bold">"validity_crc_match":</span> 0,
        <span style="font-weight: bold">"final_crc_match":</span> 1
    }
}
</pre>
</div>





