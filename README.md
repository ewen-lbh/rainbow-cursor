<p align="center">
    <img src="./logotype.png" alt="SmoothCursorify" height="150px">
    <p align="center">Apply a Microsoft Word-like smooth caret animation to multiple online editors.</p>
    <p align="center"><a href="https://addons.mozilla.org/fr/firefox/addon/smooth-cursorify/">Firefox</a>&nbsp;&bull;&nbsp;<a href="https://chrome.google.com/webstore/detail/smooth-cursorify/ohhjfajndpfpbimipmehmdkblnbelaec?hl=fr&authuser=0">Chrome</a>&nbsp;&bull;&nbsp;<a href="https://www.youtube.com/watch?v=35It5ijWl_0">Demo video</a></p>
</p>

![Mozilla Add-on downloads](https://img.shields.io/amo/dw/smooth-cursorify?label=firefox%20downloads)
![Chrome Web Store users](https://img.shields.io/chrome-web-store/users/ohhjfajndpfpbimipmehmdkblnbelaec?label=chrome%20users)

  
## Supported websites
> Please open an issue to request a new website

* Google Docs (https://docs.google.com/) · <a href="javascript:(function()%7Bvar%20cursor%20%3D%20document.getElementsByClassName(%22kix-cursor%22)%5B0%5D%0Avar%20cursor_style%20%3D%20cursor.getAttribute(%22style%22)%3B%0Acursor.setAttribute('style'%2C%20cursor_style%2B%22%20transition%3A%20all%2080ms%3B%22)%3B%7D)()%3B">bookmarklet</a>
* Overleaf (https://www.overleaf.com/) · <a href="javascript:(function()%7Bvar%20carets%20%3D%20document.querySelectorAll('.ace_cursor-layer%20.ace_cursor')%0Aconsole.info(%60%5Bsmooth-cursorify%5D%20Got%20cursor%20elements%3A%20%24%7BJSON.stringify(carets)%7D%60)%0Avar%20curCount%20%3D%200%0Acarets.forEach((caret)%20%3D%3E%20%7B%0A%20%20var%20caret_styles%20%3D%20caret.getAttribute(%22style%22)%0A%20%20caret.setAttribute(%22style%22%2C%20caret_styles%20%2B%20%22%20transition%3A%20all%2080ms%3B%22)%0A%20%20curCount%2B%2B%0A%7D)%0Aconsole.info(%60%5Bsmooth-cursorify%5D%20Applied%20styles%20to%20%24%7BcurCount%7D%20cursor(s)%60)%7D)()%3B">bookmarklet</a>

## How does it work?

Some websites use custom rendering engines to edit rich text, instead of relying on `contenteditable` or using a plain `<textarea>`/`<input>`. When using such custom methods, the cursor is not the native one, and is instead an HTML element, that can be stylized like any other. For example, Google Docs uses a 2-pixels-wide div with a black background to render its cursor.

Since those cursors are plain HTML elements, they can be **stylized**, that's where this extension comes in.

The process is simple:

1. Find the element
2. Append `transition: all 80ms` to its style tag

The problem with this is that methods using the native cursor can't really have them applied: we _can't_ access the system cursor to style it with CSS.


## Manual installation
If you want to install this extension manually:

1. Download this repository
2. Load the extension
  * On Firefox:
    1. Open <about:debugging>
    2. Click "This Firefox"
    3. Click "Load temporary addon"
    4. Navigate to the repository's folder and select the `manifest.json` file.
  * On Chrome: 
    1. Open <chrome://extensions>
    2. Toggle on "Developer mode"
    3. Click "Load unpacked extension"
    4. Select the repository's folder
