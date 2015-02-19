# Leaflet D3 Hexbin Plugin

## Chance from original

* radiusRange controls hexagon sizes for bivariate hexmaps

## What is it?
This is a Leaflet plugin that enables you to place a d3.js hexbin heatmap overlay onto your maps. This plugin is based on [the work of Steven Hall](http://www.delimited.io/blog/2013/12/1/hexbins-with-d3-and-leaflet-maps). The primary difference is that this plugin leverages the data-binding power of d3 to allow you to dynamically update the data and visualize the transitions.

## How do I use it?
To use, simply declare a hexbin layer and add it to your map. You can then add data to the layer.

```js
// Options for the hexbin layer
var options = {
  radiusRange: [1,10],      // Size of hexagons
	radius : 10,							// Size of bins
	opacity: 0.5,							// Opacity of the hexagonal layer
	lng: function(d){ return d[0]; },		// longitude accessor
	lat: function(d){ return d[1]; },		// latitude accessor
	value: function(d){ return d.length; },	// value accessor - derives the bin value
	valueFloor: 0,							// override the color scale domain low value
	valueCeil: undefined,					// override the color scale domain high value
	colorRange: ['#f7fbff', '#08306b']		// default color range for the heat map
};

// Create the hexbin layer and add it to the map
var hexLayer = L.hexbinLayer(options).addTo(map);

// Optionally, access the d3 color scale directly
// Can also set scale via hexLayer.colorScale(d3.scale.linear()...)
hexLayer.colorScale().range('white', 'blue');

// Set the data (can be set multiple times)
hexLayer.data([[lng1, lat1], [lng2, lat2], ... [lngN, latN]]);
```

## How do I include this plugin in my project?
The easiest way to include this plugin in your project, use [Bower](http://bower.io)

```bash
bower install -S leaflet-hexbin-2
```

Alternatively, you can download the source or minified javascript files yourself from the GitHub repository (they are contained in the dist directory).

Alter-alternatively, you can clone this repo and build it yourself.

You will also need to install the dependencies, which include [d3.js](http://www.d3js.org) and [leaflet.js](http://leafletjs.com/).

```bash
bower install -S d3
bower install -S leaflet
```


## How do I build this project?
There are several tools you will need to install to build this project:
* [Node](http://nodejs.org/)
* [Gulp](http://http://gulpjs.com/)
* [Bower](http://bower.io)

If you're on Mac OS, check out [Homebrew](https://github.com/mxcl/homebrew) to get node up and running easily. It's as simple as `brew install node`

First, you will need to install the build dependencies for the project using node. If you want to use the examples, you will need to install the javascript dependencies for the project using bower. Finally, to build the project and generate the artifacts in the /dist directory, you will need to build the project using gulp. 

```bash
npm install
bower install
gulp
```

## Credits
This plugin was based on [the work of Steven Hall](http://www.delimited.io/blog/2013/12/1/hexbins-with-d3-and-leaflet-maps).

[travis-url]: https://travis-ci.org/Asymmetrik/leaflet-hexbin/
[travis-image]: https://travis-ci.org/Asymmetrik/leaflet-hexbin.svg
