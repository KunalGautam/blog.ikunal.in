---
id: 149
title: "MongoDB | GeoJSON Object"
date: "2021-10-02T03:29:10+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/10/02/mongodb-geojson-object/

categories:
  - "MongoDB Learning"
---

# GeoJSON Objects

## Overview

MongoDB supports the GeoJSON object types listed on this page.

To specify GeoJSON data, use an embedded document with:

- a field named `type` that specifies the [GeoJSON object type](#) and
- a field named `coordinates` that specifies the object’s coordinates. If specifying latitude and longitude coordinates, list the **longitude** first and then **latitude**:
  - Valid longitude values are between `-180` and `180`, both inclusive.
  - Valid latitude values are between `-90` and `90`, both inclusive.

```
<field>: { type: <GeoJSON type> , coordinates: <coordinates> }

```

MongoDB geospatial queries on GeoJSON objects calculate on a sphere; MongoDB uses the [WGS84](https://docs.mongodb.com/manual/reference/geojson/../glossary/#term-wgs84) reference system for geospatial queries on GeoJSON objects.

## `Point`

The following example specifies a GeoJSON [Point](https://tools.ietf.org/html/rfc7946#section-3.1.2):

```
{ type: "Point", coordinates: [ 40, 5 ] }

```

## `LineString`

The following example specifies a GeoJSON [LineString](https://tools.ietf.org/html/rfc7946#section-3.1.4):

```
{ type: "LineString", coordinates: [ [ 40, 5 ], [ 41, 6 ] ] }

```

## `Polygon`

[Polygons](https://tools.ietf.org/html/rfc7946#section-3.1.6) consist of an array of GeoJSON `LinearRing` coordinate arrays. These `LinearRings` are closed `LineStrings`. Closed `LineStrings` have at least four coordinate pairs and specify the same position as the first and last coordinates.

The line that joins two points on a curved surface may or may not contain the same set of co-ordinates that joins those two points on a flat surface. The line that joins two points on a curved surface will be a geodesic. Carefully check points to avoid errors with shared edges, as well as overlaps and other types of intersections.

### Polygons with a Single Ring

The following example specifies a GeoJSON `Polygon` with an exterior ring and no interior rings (or holes). The first and last coordinates must match in order to close the polygon:

```
{
  type: "Polygon",
  coordinates: [ [ [ 0 , 0 ] , [ 3 , 6 ] , [ 6 , 1 ] , [ 0 , 0  ] ] ]
}

```

For Polygons with a single ring, the ring cannot self-intersect.

### Polygons with Multiple Rings

For Polygons with multiple rings:

- The first described ring must be the exterior ring.
- The exterior ring cannot self-intersect.
- Any interior ring must be entirely contained by the outer ring.
- Interior rings cannot intersect or overlap each other. Interior rings cannot share an edge.

The following example represents a GeoJSON polygon with an interior ring:

```
{
  type : "Polygon",
  coordinates : [
     [ [ 0 , 0 ] , [ 3 , 6 ] , [ 6 , 1 ] , [ 0 , 0 ] ],
     [ [ 2 , 2 ] , [ 3 , 3 ] , [ 4 , 2 ] , [ 2 , 2 ] ]
  ]
}

```

![Diagram of a Polygon with internal ring.](:/bc4a87391cc64a6c99376c26c57b0fc8)

## `MultiPoint`

Requires [Versions](https://docs.mongodb.com/manual/reference/geojson/../../core/2dsphere/#dsphere-v2)

GeoJSON [MultiPoint](https://tools.ietf.org/html/rfc7946#section-3.1.3) embedded documents encode a list of points.

```
{
  type: "MultiPoint",
  coordinates: [
     [ -73.9580, 40.8003 ],
     [ -73.9498, 40.7968 ],
     [ -73.9737, 40.7648 ],
     [ -73.9814, 40.7681 ]
  ]
}

```

## `MultiLineString`

Requires [Versions](https://docs.mongodb.com/manual/reference/geojson/../../core/2dsphere/#dsphere-v2)

The following example specifies a GeoJSON [MultiLineString](https://tools.ietf.org/html/rfc7946#section-3.1.5):

```
{
  type: "MultiLineString",
  coordinates: [
     [ [ -73.96943, 40.78519 ], [ -73.96082, 40.78095 ] ],
     [ [ -73.96415, 40.79229 ], [ -73.95544, 40.78854 ] ],
     [ [ -73.97162, 40.78205 ], [ -73.96374, 40.77715 ] ],
     [ [ -73.97880, 40.77247 ], [ -73.97036, 40.76811 ] ]
  ]
}

```

## `MultiPolygon`

Requires [Versions](https://docs.mongodb.com/manual/reference/geojson/../../core/2dsphere/#dsphere-v2)

The following example specifies a GeoJSON [MultiPolygon](https://tools.ietf.org/html/rfc7946#section-3.1.7):

```
{
  type: "MultiPolygon",
  coordinates: [
     [ [ [ -73.958, 40.8003 ], [ -73.9498, 40.7968 ], [ -73.9737, 40.7648 ], [ -73.9814, 40.7681 ], [ -73.958, 40.8003 ] ] ],
     [ [ [ -73.958, 40.8003 ], [ -73.9498, 40.7968 ], [ -73.9737, 40.7648 ], [ -73.958, 40.8003 ] ] ]
  ]
}

```

## `GeometryCollection`

Requires [Versions](https://docs.mongodb.com/manual/reference/geojson/../../core/2dsphere/#dsphere-v2)

The following example stores coordinates of GeoJSON type [GeometryCollection](https://tools.ietf.org/html/rfc7946#section-3.1.8):

```
{
  type: "GeometryCollection",
  geometries: [
     {
       type: "MultiPoint",
       coordinates: [
          [ -73.9580, 40.8003 ],
          [ -73.9498, 40.7968 ],
          [ -73.9737, 40.7648 ],
          [ -73.9814, 40.7681 ]
       ]
     },
     {
       type: "MultiLineString",
       coordinates: [
          [ [ -73.96943, 40.78519 ], [ -73.96082, 40.78095 ] ],
          [ [ -73.96415, 40.79229 ], [ -73.95544, 40.78854 ] ],
          [ [ -73.97162, 40.78205 ], [ -73.96374, 40.77715 ] ],
          [ [ -73.97880, 40.77247 ], [ -73.97036, 40.76811 ] ]
       ]
     }
  ]
}

```

←
