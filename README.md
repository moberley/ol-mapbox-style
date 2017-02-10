# ol-mapbox-style

Converts Mapbox Style objects for vector tile layers into OpenLayers style functions.

## Getting started

To use a standalone build of ol-mapbox-style, just include 'dist/olms.js' on your HTML page. Otherwise just import the ol-mapbox-style module, like in the snippet below.

The code below creates a Mapbox Streets v7 layer with the bright v9 style:

```js
import { apply } from 'ol-mapbox-style';

var key = 'Your Mapbox Access Token here';
apply('map', 'https://api.mapbox.com/styles/v1/mapbox/bright-v9?access_token=' + key);
```

Only commonly available system fonts and [Google Fonts](https://developers.google.com/fonts/) will automatically be available for text defined in the Mapbox Style object. It is the responsibility of the application to load other fonts.

To apply a subset of the layers defined in the Mapbox Style layer to a custom OpenLayers layer, use the `applyStyle()` function.

To apply the properties of the Mapbox Style's `background` layer to the map, use the `applyBackground()` function.

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### applyStyle

Applies a style function to an `ol.layer.VectorTile` or `ol.layer.Vector`
with an `ol.source.VectorTile` or an `ol.source.Vector`. The style function
will render all layers from the `glStyle` object that use the specified
`source`, or a subset of layers from the same source. The source needs to be
a `"type": "vector"` or `"type": "geojson"` source.

**Parameters**

-   `layer` **ol.layer.VectorTile** OpenLayers layer.
-   `glStyle` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object))** Mapbox Style object.
-   `source` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** `source` key or an array of layer `id`s from the
    Mapbox Style object. When a `source` key is provided, all layers for the
    specified source will be included in the style function. When layer `id`s
    are provided, they must be from layers that use the same source.

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)** Promise which will be resolved when the style can be used
for rendering.

### applyBackground

Applies properties of the Mapbox Style's first `background` layer to the map.

**Parameters**

-   `map` **ol.Map** OpenLayers Map.
-   `glStyle` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Mapbox Style object.

### apply

Loads and applies a Mapbox Style object to an OpenLayers Map.

**Parameters**

-   `map` **(ol.Map | [HTMLElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) | stribng)** Either an existing OpenLayers Map
    instance, or a HTML element, or the id of a HTML element that will be the
    target of a new OpenLayers Map.
-   `style` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Url pointing to a Mapbox Style object. When using
    Mapbox APIs, the url must contain an access token and look like
    `https://api.mapbox.com/styles/v1/mapbox/bright-v9?access_token=[your_access_token_here]`.

Returns **ol.Map** The OpenLayers Map instance that will be populated with the
contents described in the Mapbox Style object.

## Building the library

    npm install

The resulting binary (`olms.js`) will be in the `dist/` folder. To see the library in action, navigate to `example/index.html`.
