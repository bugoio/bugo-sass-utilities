# Bugo SASS Utilities (docs in progress)

A Hugo Module that contains Bugo specific Sass functions, mixins &amp; variables

## Installation

Before starting check the list below:

* Your Hugo project must use Hugo v0.58.3
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

Creates a variables file in your local build folder from all files labeled ```*-vars.scss``` at build time.

* Location: ```/public/site-variables-example.scss```
* includes ```**/*-global-variables.scss``` first