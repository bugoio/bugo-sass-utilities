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

This partial consolidates all SASS variables stored in your project's assets folders. Since this runs at build time it uses Hugo's "consoloidated" assets directory. 

Files must be named one of two ways to be included.

* *-global-variables.scss - Included at the top of the consolidated file alphabetically.
* *-vars.scss - Included alphabetically after the global variables

##### Using the partial template

Add the partial to your ```/layouts/_default/baseof.html``` template. Anywhere will do. This partial does not output any markup. The partial call below is included in the bugo-stylesheets partial. If you're already using bugo-stylesheets, you don't need to call it again.

```GO
{{ partial "utilities/bugo-sass-utilities" . }}
```

Creates a variables file in your local build folder from all files labeled ```*-vars.scss``` at build time.

* Location: ```/public/site-variables-example.scss```
* includes ```**/*-global-variables.scss``` first

#### bugo-stylesheets

##### Overview

This partial returns a permalink to a consolidated CSS resource.

* Processes ```.scss`` files in Hugo's assetDir (```/assets`` by default)
* Excludes SASS partials (```_*.scss```)
* Hugo Environment sensitive. Not NODE_ENV!
  * production - compressed, no source maps
  * All others - expanded with source maps

##### Using the partial template
```GO
{{ $stylesheet := partial "utilities/bugo-stylesheets" . }}
<link rel="stylesheet" href="{{ $stylesheet }}" media="screen" />
```
