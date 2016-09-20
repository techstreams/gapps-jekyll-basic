## Overview

Basic [Jekyll](https://jekyllrb.com/) theme for local [Google Apps Script](https://www.google.com/script/start/
) UI development.

**Useful for:**

* Local [Add-on](https://developers.google.com/apps-script/add-ons/) and [Web Application](https://developers.google.com/apps-script/guides/web) UI development
* Rapid UI prototyping with [Jekyll's auto-regeneration feature](https://jekyllrb.com/docs/usage/)


**Theme includes:**

* Reference to [CSS](https://developers.google.com/apps-script/add-ons/css) required for all [Google Apps Add-ons](https://developers.google.com/apps-script/add-ons/)
* Flexible configuration

**Project Directory Structure:**

```
gapps-jekyll-basic/
|-- _includes/
|   |-- example/
|       |-- search.html
|   |-- executionapi/
|       |-- executionapi.html
|       |-- gsapi.html
|   |-- branding.html
|   |-- head.html
|   |-- css.html
|   |-- js.html
|-- _layouts/
|   |-- default.html
|-- _config.yml
|-- apiexample.html
|-- index.html

```


**Configuration _(`_config.yml`)_:**

* Development & Production modes
* Multiple window sizing options: `sidebar`, `dialog` or `full`
* *Optional:* jQuery inclusion
* *Optional:* Non-scrolling branding area inclusion
* *Optional:* Test integration through the [Execution API](https://developers.google.com/apps-script/guides/rest/)

```
# Jekyll Google Apps Script Basic Configuration

config:
  production: false
  screen: 
    size: "dialog"
    width: "500"
    height: "500"
    branding: true 
  jquery: 
    include: true 
    version: "2.2.4"
  executionApi:
    include: false 
    clientId: "OAUTH CLIENT ID"
    scriptId: "SCRIPT ID" 
```

<br>

## Installation

1) [Install](https://jekyllrb.com/docs/installation/) Jekyll



2) Clone this project

```
git clone https://github.com/techstreams/gapps-jekyll-basic.git
```


3) Navigate to project directory

```
cd gapps-jekyll-basic
```


4) Run Jekyll

```
jekyll serve
```


5) View in the local development server:  [http://localhost:4000](http://localhost:4000)


<br>

## Getting Started


**DEVELOPMENT MODE:**

1) In `_config.yml`:

* Set `production` option to `false`


* Set `screen size` option to desired value:  `sidebar`, `dialog` or `full`  
> *If the screen size is `dialog`, set the screen `width` and `height` options to desired values ... `sidebar` and `full` 'width' and 'height' values are preset*

2) Start/Restart the Jekyll server in project directory

```
jekyll serve
``` 

*or*

```
jekyll build --watch
```

3) Add any client-side Javascript to `_includes/js.html`


4) Add any custom CSS to `_includes/css.html`


5) Make iterative UI modifications to `index.html` ... ***Jekyll will auto-regenerate the site***


<br>

**PRODUCTION MODE:**

1) In `_config.yml`:

* Set `production` option to `true`

2) Start/Restart the Jekyll server and wait for site to build 

```
jekyll serve
``` 

*or*

```
jekyll build
```

3) Copy the generated `_site/index.html` file to the Google Apps Script environment

<br>


***To Include Branding:*** 

1) In `_config.yml`:

* Set the `screen branding` option to `true`

2) Start/Restart the Jekyll server


3) Update the `_includes/branding.html` file with branding information



<br>

***To Include jQuery:*** 

1) In `_config.yml`:

* Set the `jQuery include` option to `true`


* Set the `jQuery version` option the desired *[Google CDN hosted jQuery version](https://developers.google.com/speed/libraries/#jquery)*


2) Start/Restart the Jekyll server


<br>


## Test Using the Execution API

**DEVELOPMENT MODE:**

Test UI in ***Development Mode*** by integrating with the [Google Apps Script Execution API](https://developers.google.com/apps-script/guides/rest/):


1) [Create a target script project](https://developers.google.com/apps-script/guides/rest/quickstart/target-script) for the Google Apps Script Execution API *(save the __Target Script ID__ for configuration)*

2) [Turn on the Google Apps Script Execution API](https://developers.google.com/apps-script/guides/rest/quickstart/js) *(save the __OAuth Client ID__ for configuration)*

> *__NOTE:__ Jekyll's local development server runs on port 4000 by default.  Set the __Authorized JavaScript origins__ field to `http://localhost:4000` when creating the __OAuth Client ID__ in the [Google Development Console](https://console.developers.google.com)*

3) In `_config.yml`:

* Set `production` option to `false`


* Set the `executionApi include` option to `true`


* Set the `executionApi clientId` option to **OAuth Client ID** created in *Step 2*


* Set the `executionApi scriptId` option to **Script ID** created in *Step 1*

4) Start/Restart the Jekyll server

5) Write Execution API calls

> *See `apiexample.html` and `_includes/executionapi/executionapi.html` files for an example*

<br>

**PRODUCTION MODE:**

Once the UI is ready ... export in ***Production Mode***:

1) Write [Google Apps Script server calls](https://developers.google.com/apps-script/guides/html/communication)

> *See `apiexample.html` and `_includes/executionapi/gsapi.html` files for an example*

2) In `_config.yml`:

* Set `production` option to `true`


* Set the `executionApi include` option to `true`

3) Start/Restart the Jekyll server and wait for site to build 

```
jekyll serve
``` 

*or*

```
jekyll build
```

4) Copy the generated `_site/apiexample/index.html` file *(or your corresponding generated `_site/.../index.html`)* to the Google Apps Script environment 

<br>

## Special Notes

* This Jekyll theme builds the UI as a ***single `_site/index.html`*** file due to client-side CSS *(`_includes/css.html`)*, Javascript *(`_includes/js.html`)* and *(optional backend server code ... `_includes/executionapi/gsapi.html`)* being ***'included'*** in the Jekyll build *(see the [Jekyll documentation on 'includes'](https://jekyllrb.com/docs/templates/#tags) for more information)*
> *If you configure CSS, Javascript or backend server code to be a static asset in your your Jekyll build, remember to include these files in the production Google Apps Script project in addition to the generated `_site/index.html` file*

* To change the __title__ element in the generated UI html ... modify the `title` option in `_config.yml`

```
title: "Jekyll Google Apps Script Basic Theme"
```

* Any configuration changes to `_config.yml` require a Jekyll server restart.


<br>


## License

Project is [licensed MIT](LICENSE).

© [Laura Taylor](https://github.com/techstreams)