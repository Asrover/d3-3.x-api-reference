> [API Reference](API-Reference.md) ▸ [Geometry](Geometry.md) ▸ **Voronoi Geom**

**The [D3 4.0 API Reference](https://github.com/d3/d3/blob/master/API.md) has moved. This page describes the D3 3.x API.**

Voronoi layouts are particularly useful for invisible interactive regions, as demonstrated in Nate Vack’s [Voronoi picking](http://bl.ocks.org/njvack/1405439) example. See Tovi Grossman’s paper on [bubble cursors](http://www.tovigrossman.com/BubbleCursor) for a related concept.

<a name="voronoi" href="#voronoi">#</a> d3.geom.<b>voronoi</b>()

<a href="http://bl.ocks.org/mbostock/4060366"><img src="http://bl.ocks.org/mbostock/raw/4060366/thumbnail.png" width="202"></a>

Creates a Voronoi layout with default accessors.

<a name="_voronoi" href="#_voronoi">#</a> <b>voronoi</b>(<i>data</i>)

Returns an array of polygons, one for each input vertex in the specified *data* array. Each polygon is an array of points, and each point is a two-element array of _x_ and _y_ positions.

If any vertices are coincident or have `NaN` positions, *the behavior of this method is undefined*: most likely, invalid polygons will be returned! You should filter invalid vertices, and consolidate coincident vertices, before calling this function.

<a name="x" href="#x">#</a> voronoi.<b>x</b>([<i>x</i>])

If *x* is specified, sets the x-coordinate accessor. If *x* is not specified, returns the current x-coordinate accessor, which defaults to:

```js
function(d) { return d[0]; }
```

<a name="y" href="#y">#</a> voronoi.<b>y</b>([<i>y</i>])

If *y* is specified, sets the y-coordinate accessor. If *y* is not specified, returns the current y-coordinate accessor, which defaults to:

```js
function(d) { return d[1]; }
```

<a name="clipExtent" href="#clipExtent">#</a> voronoi.<b>clipExtent</b>([<i>extent</i>])

If *extent* is specified, sets the clip extent of the Voronoi layout to the specified bounds and returns the layout. The *extent* bounds are specified as an array [​[<i>x0</i>, <i>y0</i>], [<i>x1</i>, <i>y1</i>]​], where <i>x0</i> is the left side of the extent, <i>y0</i> is the top, <i>x1</i> is the right and <i>y1</i> is the bottom. If *extent* is `null`, no clipping is performed. If *extent* is not specified, returns the current clip extent which defaults to `null`.

See [this example](http://bl.ocks.org/mbostock/4237768). Use of a clip extent is strongly recommended, as unclipped polygons may have large coordinates which do not display correctly.

Alternatively, you can also employ custom clipping without specifying a size, either in SVG or by post-processing with [polygon.clip](Polygon-Geom.md#clip).

<a name="links" href="#links">#</a> voronoi.<b>links</b>(<i>data</i>)

Returns the Delaunay triangulation of the specified *data* array as an array of links. Each link has the following attributes:

* source - the source node (an element in *data*).
* target - the target node (an element in *data*).

The <a href="http://bl.ocks.org/mbostock/1073373">Force-Directed States of America</a> uses an array of such links to create a force-directed graph.

<a name="triangles" href="#triangles">#</a> voronoi.<b>triangles</b>(<i>data</i>)

<a href="http://bl.ocks.org/mbostock/4341156"><img src="http://bl.ocks.org/mbostock/raw/4341156/thumbnail.png" width="202"></a>

Returns the <a href="https://en.wikipedia.org/wiki/Delaunay_triangulation">Delaunay triangulation</a> of the specified *data* array as an array of triangles.  Each triangle is a three-element array containing elements from *data*.
