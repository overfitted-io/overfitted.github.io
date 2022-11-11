---
layout: page
title: Get Started
permalink: /get-started/
emphasis: true
---

In order to use the services hosted here, an **API key** must be included in each request. This API key is issued **per account** and provides access to all functionalities which are listed as available on our platform.

The services operate using a **credits system**: each account has a number of credits, and each service consumes a predefined amount of these credits when queried using the account's API key.

# Free Testing

A new account will include a number of **free credits** (currently **10**). These will allow you to run different tests and decide whether the services are suitable for your project.
For instance, querying the OCR / HTR service consumes around **0.01 credits / 1000 characters**.


These credits are available with:
- no commitments
- no credit card information
- no expiration time

You will not be charged if you run out of credits.
Should you find a service to be matching your needs, please contact us for further discussions.


# Get Your API Key

We require a **Google**-based **authentication** in order to issue a new API key for your account. You will be informed by Google in the pop-up window **what information will be shared** with overfitted.io. 

The information we collect is similar to the information supplied in any other registration form, when creating an account. We will not share this information with any other party.

Once you successfully authenticate, a modal will be shown containing your account details and **API key**. Please make sure you're not blocking those or JavaScript. If you ever need your API key again, just redo the authentication step.

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