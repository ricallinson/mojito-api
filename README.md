# Mojito API

Rics short list of Mojito API's to use.

## Quick Start

The fastest way to see __Mojito__ running;

    npm i mojito -g

In an empty directory create _./mojits/simple/controller.common.js_ with the following content;

    YUI.add("simple-ctrl", function(Y, NAME) {
        Y.namespace("mojito.controllers")[NAME] = {
            index: function(ac) {
                ac.done("Hello world");
            }
        };
    });

In the same directory run the start command;

    mojito start

Open [http://localhost:8666/@simple/index](http://localhost:8666/@simple/index) in a browser.

# Standard Addons

* [ac.params](#acparams)
* [ac.composite](#accomposite)
* [ac.assets](#acassets)
* [ac.models](#acmodels)
* [ac.cookie](#accookie)
* [ac.http](#achttp)

# Custom Addons

* [ac.html](#achtml)

## ac

An object __addons__ attach to and the only argument to a controller function. The __ac__ has the following functions attached by default.

### ac.done

Can only be called once. Passes data and/or meta upstream and signals there is no more to be sent. Preforms the same operations as [ac.flush](#acflush).

### ac.flush

Can be called many times. Passes data and/or meta upstream.

    ac.flush("text");

    // Looks for a template to render with the same name as the containing function
    ac.flush({msg: "text"});

    // Looks for a template to render
    ac.flush({msg: "text"}, "index");
    ac.flush({msg: "text"}, {view: {name: "index"}});

    // renders data as JSON
    ac.flush({msg: "text"}, "json");

    // renders data as XML
    ac.flush({msg: "text"}, "xml");

## ac.params

An __addon__ for dealing with inputs.

### ac.params.merged

This function returns an input value with the lookup performed in the following order:

    ac.params.route();
    ac.params.body();
    ac.params.url();

Calling [ac.params.body](#acparamsbody), [ac.params.route](#acparamsroute), and [ac.params.url](#acparamsurl) should be favored for clarity.

### ac.params.url

This function is an object containing the parsed query-string, defaulting to {}.

    // GET /search?q=mojitos+js
    ac.params.url("q");
    // => "mojitos js"

### ac.params.route

This function contains properties mapped to the named route "parameters". For example if you have the route /user/:name, then the "name" property is available to you as ac.params.route("name"). This object defaults to {}.

    // GET /user/mojito
    api.params.route("name");
    // => "mojito"

### ac.params.body

### ac.params.files

## ac.composite

### ac.composite.execute

## ac.assets

### ac.assets.addCss

### ac.assets.addJs

### ac.assets.addBlob

### ac.assets.addAsset

### ac.assets.addAssets

### ac.assets.preLoadImage

### ac.assets.preLoadImages

## ac.models

### ac.models.get

## ac.cookie

### ac.cookie.set

### ac.cookie.get

## ac.http

__Server Only__

### ac.http.addHeader

### ac.http.setHeader

### ac.http.getHeader

### ac.http.getHeaders

### ac.http.redirect

## ac.html

From the bundle [mojito-client-lite](https://github.com/ricallinson/mojito-client-lite) and used in place of the HTMLFrameMojit.
