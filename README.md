# Bugo SASS Utilities (docs in progress)

A Hugo Module that contains Bugo specific Sass functions, mixins &amp; variables

## Installation

Before starting check the list below:

* Your Hugo project must use Hugo v0.58.3 or greater
* Your Hugo project must be in a git repository
* Your Huog project must be a Hugo Module

If your project isn't a Hugo Module.
```BASH
hugo mod init
```

Get this module.
```BASH
hugo mod get github.com/bugoio/bugo-sass-utulities
```

Add it to your Hugo config file (shown in YAML).
```YAML
module:
  imports:
  - disable: false
    ignoreConfig: false
    path: github.com/bugoio/bugo-sass-utilities
```

## Usage

### Partials

#### bugo-sass-variables

##### Overview

This template consolidates all SASS variables stored in your project's assets folders. Since this runs at build time it uses Hugo's "consoloidated" assets directory. 

Files must be named one of two ways to be included.

* *-global-variables.scss - Included at the top of the consolidated file alphabetically.
* *-vars.scss - Included alphabetically after the global variables

#### Using the partial template

Add the partial to your ```/layouts/_default/baseof.html``` template. Anywhere will do. This partial does not output any markup.
```
{{ partial "bugo-sass-utilities" . }}
```

Creates a variables file in your local build folder from all files labeled ```*-vars.scss``` at build time.

* Location: ```/public/site-variables-example.scss```
* includes ```**/*-global-variables.scss``` first
