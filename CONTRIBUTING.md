# Contributing

Prior to contributing, please examine the [Code of Conduct][coc] to honor
these at all times.

[coc]: ./CODE_OF_CONDUCT.md

The steps to complete prior to submitting a PR are:

- [ ] [compile CSS](#compile-css)
- [ ] [format source](#format-source)
- [ ] [update screenshots](#update-screenshots)

> The assumption is made that you are using a Node.js runtime in order to
> leverage the tooling used in formatting the source, transpiling SCSS to CSS
> and capturing screenshots.

## Compile CSS

Run `npx node-sass PATH_TO_INPUT_SCSS_FILE PATH_TO_OUTPUT_CSS_FILE` to compile
SCSS into CSS

## Format Source

Run `npx prettier --write .` to "prettify" source.

## Update Screenshots

The table below provides the details for the screenshots which are to be
captured for the different templates..

| Output file       | Width (px) | Height (px) | [Device Profile in Chrome DevTools][chrome-screens] | [Responsive Design Mode in Firefox][firefox-screens] |
| :---------------- | ---------: | ----------: | :-------------------------------------------------- | :--------------------------------------------------- |
| preview-large.png |       1440 |         900 | Laptop with HiDPI                                   | Laptop with HiDPI                                    |
| preview-small.png |        375 |         557 | iPhone 6/7/8                                        | iPhone 6/7/8                                         |

### Automated

The easiest way to produce the needed screenshots, is by using the provided
Dockerfile and package.json to spawn a Node.js environment with the tooling to
automatically capture the needed screenshots.

#### Node.js on host

Prerequisites:
- [Node.js](https://nodejs.org/en/)

Perform the following steps to automatically generate screenshots for
a given template:
1. Install NPM packages by running `npm install`
2. Capture screenshots by running `npm run capture TEMPLATE_DIRECTORY` where
   `TEMPLATE_DIRECTORY` can be substituted for the name of a subdirectory
   containing the template (e.g.: "enchanted")

#### Node.js in Docker

Prerequisites:
- [Docker](https://docs.docker.com/get-docker/)

Perform the following steps to automatically generate screenshots for
a given template:
1. Produce the needed image by running `make dev-image`
2. Enter a Bash shell in a container by the previously created image by running
   `make bash`
3. Install NPM packages by running `npm install`
4. Capture screenshots by running `npm run capture TEMPLATE_DIRECTORY` where
   `TEMPLATE_DIRECTORY` can be substituted for the name of a subdirectory
   containing the template (e.g.: "enchanted")

### Manual

Prerequisites:
- local webserver if you have Python installed you can simply run `python -m
  SimpleHTTPServer` for version [2.x][py-simplehttpserver] or `python -m
  http.server` for version [3.x][py-http-server] whenever a webserver is needed
- [Firefox][firefox] or [Chrome][chrome]/[Chromium][chromium]

Perform the following steps to manually generate screenshots for a
given template:
1. Start local webserver (e.g.: `python -m http.server`)
2. Update screenshots with [Firefox](#firefox) or
   [Chrome/Chromium](#chromechromium)

#### Firefox

Open Firefox and perform the following steps to capture the needed
screenshots:
1. Open [Web Console][firefox-screenshots] (by pressing **Ctrl + Shift + K**
   navigating from the menu "Tools" > "Web Developer" > "Web Console")
2. Enable the responsive design mode (by clicking the "Responsive Design Mode"
   button or pressing **Ctrl + Shift + M**)
3. Select the device for which to capture screenshot
4. Click "Take a screenshot of the viewport" Open the command prompt (by
   clicking "Run Command" from the dev tools menu or pressing **Ctrl + Shift +
   P**)
5. Enter `:screenshot` or select "Capture full size screenshot" into the
   command prompt and save
6. Repeat for the devices listed in the table below

#### Chrome/Chromium

Open Chrome/Chromium and perform the following steps to capture
the needed screenshots:
1. [Open Developer Tools][open-chrome-devtools] (by right clicking anwhere on
   the page and selecting "Inspect" or pressing **Ctrl + Shift + I**)
2. Enable the device toolbar (by clicking the "Toggle Device Toolbar" icon or
   pressing **Ctrl + Shift + M**)
3. Select the device for which to capture screenshot
4. Open the command prompt (by clicking "Run Command" from the dev tools menu
   or pressing **Ctrl + Shift + P**)
5. Enter `:screenshot` or select "Capture full size screenshot" into the
   command prompt and save
6. Repeat for the devices listed in the table below

[chrome]: https://www.google.com/chrome/
[chromium]: https://www.chromium.org/Home
[firefox]: https://www.mozilla.org/en-US/firefox/new/
[moz-screenshots]: https://developer.mozilla.org/en-US/docs/Tools/Taking_screenshots
[py-simplehttpserver]: https://docs.python.org/2/library/simplehttpserver.html
[py-http-server]: https://docs.python.org/3/library/http.server.html
[2ality-py-server]: https://2ality.com/2014/06/simple-http-server.html
[moz-py-server]: https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server
[chrome-screens]: https://developers.google.com/web/tools/chrome-devtools/device-mode#viewport
[firefox-screens]: https://developer.mozilla.org/en-US/docs/Tools/Responsive_Design_Mode
[open-chrome-devtools]: https://developers.google.com/web/tools/chrome-devtools/#open
