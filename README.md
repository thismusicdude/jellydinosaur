# DinosaurBooks
A no bullshit, very compatible, super fast, and JavaScript ES3 compliant Jellyfin client (front-end) for **books**: browse your Jellyfin e-book library and download the books, for example straight onto an e-reader such as a Tolino.

It is a static ~30kb HTML webpage, which can be uploaded to any HTTP web server or hosted locally.

To host your instance of DinosaurBooks locally and quick, use on the upload folder: python3 -m http.server 20005

You may want to setup this app with an integrated reverse proxy on your LAN which you can do with: node serve-with-proxy.js

*Reverse proxy is especially useful if you need very old operating systems/browsers (or e-reader browsers) which lack modern TLS to access any kind of Jellyfin server requiring SSL.*

## Tech stack
- Pure HTML/ES3 JS (index.html)
- (Optional) NodeJS if you want to use the easy SSL escalation reverse proxy script (serve-with-proxy.js) and the build-minify.js minification script I provide

## Features
- Internationalization (french & english)
- Can login on JellyFin through an API key or a login + password
- Books: browse, search and filter your e-books by genre (the file format, e.g. EPUB/PDF, is shown in the list), see author, publisher and description, then download the original file with a plain link, so it also works from an e-reader's built-in browser (e.g. Tolino)
- Modern browsers are not excluded and should be happy to use this front-end too, the main aspect you may want it is for performance & its minimalistic approach. Here you won't load megabytes of stuff and executing plenty of javascript for fancy animations and UI stuff & front frameworks.

## Downloading to an e-reader (Tolino)
Open DinosaurBooks in the e-reader's built-in browser, log in, pick a book and tap "Download": the book is saved to the e-reader and shows up in its library. Tolino readers open EPUB, PDF and TXT (no MOBI/AZW). The Jellyfin account needs the "Allow media downloads" permission. If the e-reader's browser cannot open your Jellyfin server over HTTPS, use the reverse proxy (node serve-with-proxy.js) from a computer on your LAN.

## What is the minimal configuration
Your browser need to support LocalStorage and ES3 JavaScript. Expect early-2000 browsers to work which covers well the native browsers from the Windows XP/PowerPC Macs era.

# What can't run on very old browsers
- The browser will not save/remember any of your settings over different sessions when local storage is missing. LocalStorage is supported since Chrome 4 (2009), Firefox 3.5 (2009), Opera 10.5 (2010), Safari 4 (2009) on major desktop browsers.
- Some very old browsers are very annoying about cross-domain, so you will need to host DinosaurBooks on the same domain (if you own the JellyFin server) or use the reverse proxy that I provide from a modern computer on your LAN
- Browser need to be JavaScript ES3 (1999) compliant. DinosaurBooks was designed with interactivity so JavaScript ES3 must be available and enabled browser-side.

## Artificial intelligence usage
AI-assisted code using a bit of local Google Gemma (but it was just so slow/limited) and a lot of Claude Code. Sorry, I don't have weeks/months to really master 20 year (ES3 is from 1999) tech and I believe at this point I am proud enough to share that work because I believe it works as great if not best from a production I would had done alone. Also most of the human work there is not even that fun, and just about interacting properly with the Jellyfin API by using old ES3 ways of doing so.

Outside of the code, everything is human efforts, including but not limited to:
- QA testing
- Writing the specs
- Iterating. Plenty of iterating & testing using a real browser & several old machines
- Driving the AI with knowledge of good practices for performance & to fit my quality standards (for example, search here is not going to redraw the page instantly, but instead will wait a bit so if you type several characters at once it will search only once because filtering is a costly operation especially for old machines)
- Some little changes on the code & reviews on what produced the gen-AI
- Writing GitHub commits, documentation, and this README. In english by a french native, so there may be mistake but I want control on what text you are going to see, I don't want to flood you with slop/low quality/out of point info you're not even going to ever read.
- Writing social media posts and answering to comments from the community

## Supporting your work
If you wanna help me to cover the costs of this dev (time spent + API costs for AI tools) and if this app is useful to you, a tip will be greatly apprecied thank you very much: https://www.patreon.com/Olsro
