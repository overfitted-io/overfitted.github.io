---
layout: section-tab
title: Requests Served
---

<div style="text-align: center">
    <img src="{{ '/assets/img/icons/ic_req_res.svg' | relative_url }}" style="margin:auto; display: inline-block; width: 128px; height: 128px; pointer-events: none; user-select: none;">
    <div style="display: inline-block; vertical-align: middle">
    <p id="num_requests" style="color: orangered; font-size: 50px; font-family: 'Dosis', sans-serif; font-weight: bold; margin-bottom: 0px;">?</p>
    <p style="color: darkcyan; font-family: 'Dosis', sans-serif; font-weight: bold;">requests served... so far</p>
    </div>
</div>


<script>
    function get_current_requests(obj) 
    {
        var req = new XMLHttpRequest()

        req.onreadystatechange = function() {
            if (req.readyState == 4 && req.status == 200) {
                num_requests = req.response

                suffix = ''

                if (num_requests > 1e6)
                {
                    suffix = 'm'
                    num_requests = (num_requests / 1e6).toFixed(2)
                }
                else
                    if (num_requests > 1e3)
                    {
                        suffix = 'k'
                        num_requests = (num_requests / 1e3).toFixed(2)
                    }
                

                document.getElementById('num_requests').innerHTML = num_requests + suffix;
            }
        }

        req.open('GET', 'https://db-api.api.overfitted.io/get-num-requests', true)
        req.send(null)
    }

    window.addEventListener('load', function() {
        get_current_requests()
    }, false);
</script>

