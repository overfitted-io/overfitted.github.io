---
layout: post
title:  "ScreenOCR - Fast OCR as a Windows Keyboard Shortcut"
date:   2022-11-16 11:52:19 +0300
categories: ocr
index: true
---



Recently, the **ScreenOCR** application was released for testing. 

It is a lightweight tool which allows its users to quickly submit **regions** of their **screen** for **OCR** (and **HTR** in the future) and, in return, receive selectable text. It integrates into the **Windows** operating systems as a **keyboard shortcut**.

**ScreenOCR** relies on the [Glyph](https://overfitted.io/ocr/glyph-ocr-engine) engine to handle the image-to-text tasks and therefore will require an active **internet connection** and the usual **API Key**. These will be configured within the application.

On **GitHub**: [https://github.com/overfitted-io/ScreenOCR](https://github.com/overfitted-io/ScreenOCR).



## Demo

![ScreenOCR Demo](/assets/img/posts/screenocr-fast-ocr-windows-keyboard-shortcut/screenocr-demo.gif)


## Download

### Requirements

* **.NET Framework 4.5**
* **Windows** (tested on **10/Home** edition)


Check the **GitHub Releases** page: [https://github.com/overfitted-io/ScreenOCR/releases](https://github.com/overfitted-io/ScreenOCR/releases).

## Configuration

When first starting the application, the following **Configuration Window** should appear in the upper screen area.

{% include image.html
            description="**Configuration Window:** ScreenOCR's configs for the **English** language with a **Modern Antiqua** font (`en-ma`) and a hidden **API Key** for authentication"
            size="60%"
            url="/assets/img/posts/screenocr-fast-ocr-windows-keyboard-shortcut/configs-window.png" %}

If the window isn't shown or you need to re-open it, hit the following keyboard shortcuts, in this order:
1. **[Win]**-**[Shift]**-**[Q]**  (this should darken your screen since it switches to **Capture Mode**)
2. **[Shift]**-**[O]** (this should pop the **Configuration Window**)

In the **Configuration Window**, you must fill in two fields: 
* **Language**: specifies which language should be used for the targeted texts and instructs the OCR engine to make certain assumptions to improve the quality of the recognized text; see the list of [Supported Language Codes](/ocr/glyph-ocr-engine#supported-languages) 
* **API Key**: is the key you're using to authenticate on **overfitted.io** in order to use the Glyph OCR service; take a look at the [Get Started](/get-started/) page for more details on this.

Optionally, you can check the **launch at startup** box which will ensure that ScreenOCR runs automatically every time you start your computer. To undo this setting, simply uncheck the box.

Once you've completed the configs, hit the blue **Save** button.


## Usage

With **ScreenOCR**'s process actively running in background:

1. Hit the **[Win]**-**[Shift]**-**[Q]** keyboard shortcut; this should switch to **Capture Mode** and make your screen noticeably **darker**
2. While holding the **left mouse button**, draw a **rectangle** over your targeted text
3. When done, press either **[Enter]** to attempt text extraction from the aforementioned region or **[Esc]** to reset
4. If available, select & copy your text from the recently appeared window and press **[Esc]** to close it

The application is designed to non-invasively run while your computer is powered on so it is available whenever needed. 
If, for some reason, you wish to completely **close the application**, switch to **Capture Mode** (**[Win]**-**[Shift]**-**[Q]**) and then hit **[Shift]**-**[Esc]**.


## Privacy Aspects

Due to the possible actions of ScreenOCR, it can be seen as a **potential threat** by certain **anti-malware** software. This happens because globally listening for specific keyboard shortcuts, implementing screenshot-taking procedures and running on startup are common **spyware** strategies. This application, however, will not track user activities outside its scope; it will look only for its specific keyboard shortcuts and will record screen regions only when instructed to do so by the end-user.

For transparency reasons, the **entire source code** for this project is **published** in this [GitHub Repo](https://github.com/overfitted-io/ScreenOCR) and can be **easily verified** for any malicious activities.


## Future Functionalities

**ScreenOCR** serves as a more convenient interface to our cloud-based OCR engine; in this aspect, it tracks all the progress and upgrades made on our side. When support for new languages is implemented on our servers, it will also become available in the application.

If you discover incorrect behaviour or bugs strictly in the application's side, please submit a GitHub issue.
