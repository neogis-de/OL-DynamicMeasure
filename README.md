Control for OpenLayers to measure and shows measurements at the cursor
======================================================================

A fork of http://jorix.github.com/OL-DynamicMeasure
with added option to use "geodesic:true" for measurements.

Based on `OpenLayers.Control.Measure`, the **DynamicMeasure** control shows
measurements on labels that follow the cursor. This avoids having to worry
about preparing a DOM item to display measurements.

The control also has preset styles to show lines and labels, so the only thing
to do is add it to the map.

Control allows displaying lengths and headings of the segments that form a polyline or a polygon.

Examples:
---------
 * [measure-dynamic.html](http://rawgit.com/neogis-de/OL-DynamicMeasure/geodesic/examples/measure-dynamic.html) 
(dont't use https, otherwise some contents are blocked...)
Operation:
---------

Example:

```javascript
    ...
    // to mesure length
    var cMeasure = new OpenLayers.Control.DynamicMeasure(OpenLayers.Handler.Path);
    map.addControl(cMeasure);
    ...
    // ... and to start measuring
    cMeasure.activate();
    ...
    // ... and to stop it
    cMeasure.deactivate();
    ...
```

This control is now adapted to handle the methods *undo* *redo* and *cancel* of drawing handlers.

See the example [measure-dynamic.html](https://github.com/neogis-de/OL-DynamicMeasure/blob/geodesic/examples/measure-dynamic.html) (allows choose whether to use the geodesic option while measuring))

The control can use it as a `DrawFeature` control, see example [measure-and-draw.html](http://jorix.github.com/OL-DynamicMeasure/examples/measure-and-draw.html)

Documentation:
--------------
 * [API for users](http://jorix.github.com/OL-DynamicMeasure/doc/DynamicMeasure/api)
 * For developers
   * [all `DynamicMeasure` elements](http://jorix.github.com/OL-DynamicMeasure/doc/DynamicMeasure/all)

Compatibility with OpenLayers releases:
---------------------------------------
The `DynamicMeasure` control works correctly with release 2.11 or higher
including the development version.

Background
----------
According [**Yus's question in DEV**](http://osgeo-org.1803224.n2.nabble.com/Adding-Segment-Length-to-Path-tc7029815.html)
some adjustments are made to solve some problems: 
labels do not remain at the end of measure,
using the freehand the map is dirtied by the labels,
layer of the labels (`vlayer`) should be on top of the drawing layer,
allow use of immediate measure (new in 2.11) 
