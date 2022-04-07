---
layout: page
title: Get Started
permalink: /get-started/
---

In order to use the services hosted by overfitted.io, an API key must be included in each request. This API key is issued per account and provides access to all functionalities which are listed as available on our platform.

Each new API key will include a number of free resources - and each service consumes a predefined amount of these resources when queried using the aforementioned API key. This permits running a limited number of tests at no cost in order to decide whether the targeted service matches your needs.


# Your API Key

We require a Google-based authentication in order to issue a new API key for your account. You will be informed by Google in the pop-up window what information will be shared with overfitted.io.

Once logged in, a popup will reveal your API key.

<script>
    function handleCredentialResponse(obj) 
    {
        var req = new XMLHttpRequest()

        req.onreadystatechange = function() {
            if (req.readyState == 4) {
                document.getElementById('credentials_modal_content').innerHTML = JSON.stringify(JSON.parse(req.response), null, 4);
                document.getElementById('credentials_modal').style.display = "block";
                document.getElementById('credentials_modal_window').style.display = "block";

            }
        }

        req.open('POST', 'https://db-api.api.overfitted.io/register-api-key', true)
        req.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
        req.send('credential=' + obj.credential)
    }
</script>

<style>
@keyframes animatetop {
  from {opacity: 0}
  to {opacity: 1}
}

#credentials_modal
{
    display:none; 
    z-index: 9999; 
    position:fixed; 
    width: 100%; 
    height: 100%; 
    top: 0px; 
    left: 0px; 
    background-color: rgba(0, 0 , 0, 0.6);
}

#credentials_modal_window
{
    margin: 15% auto;  
    box-shadow: 1px 1px 10px 0px #444;
    border-radius: 5px;
    width: 60%;
    background-color: #FFF;
    padding: 10px; 
    border: 1px solid #444;
    animation-name: animatetop;
    animation-duration: 0.4s;
    text-align: center;
}

#credentials_modal_content
{
    text-align: left;
}

#close_credentials_modal
{
    font-size: 40px;
    margin: 10px;
}

#close_credentials_modal:hover
{
    cursor: pointer;
    color: #555;
}


</style>

<div id="credentials_modal">
    <div id="credentials_modal_window">
    
    <pre id="credentials_modal_content">
    </pre>

    <span id="close_credentials_modal" onclick="{ document.getElementById('credentials_modal').style.display = 'none'; document.getElementById('credentials_modal_window').style.display = 'none'; }">&times;</span>

    </div>
</div>

<div id="g_id_onload"
    data-client_id="979561231043-5o2h3h23ou83gfa0easjsd7hga1pkokh.apps.googleusercontent.com"
    data-callback="handleCredentialResponse"
    data-auto_prompt="false" style="display:table; margin: 0 auto;">
</div>
<div class="g_id_signin"
    data-type="standard"
    data-size="large"
    data-theme="outline"
    data-text="continue_with"
    data-shape="rectangular"
    data-logo_alignment="left" style="display:table; margin: 0 auto;">
</div>