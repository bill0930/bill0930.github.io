# Building a World

### Geometries

-  Instances of `THREE.Geometry`
-  defines the shape of object in a scene
-  made up `vertices` and `faces` 
-  `vertices`
   -  `THREE.Vector3` objects representing points in three-dimensional space
-  `faces`
   -  `THREE.Face3` objects representing triangular surface

-  `THREE.Geometry` has many subclasses that help create commonly used shape



### 3D Primitives

`Segments` parametres  split the sides sides into saller rectangles

**Cube**

```javascript
THREE.CubeGeometry(width, 
                   height, 
                   depth, 
                   widthSegments = 1,
                   heightSegments = 1,
                   depthSegments = 1)
```

**Sphere**

```js
THREE.Sphere(radius,
  horizontalSegments = 8,
  verticalSegments = 6)
```

**Polyhedra**

It is a sphere approximation based on shapes with 20, 8, or 4 sides, respectively; 

the detail parameter specifies how many times to split each edge to make more faces, making the shape more spherical.  	

```
THREE.Icosahedron(radius,
  detail = 0);
  THREE.Octahedron(radius,
  detail = 0);
  THREE.Tetrahedron(radius,
  detail = 0);
```



**Cylinder**

```js
THREE.
  CylinderGeometry(
  radiusTop,
  radiusBottom, 
  height,
  radiusSegments = 8, //radiusSegments is the number of edges connecting the top and bottom faces,down to curved surface
  heightSegments = 1,  // heightSegments is the number of rings of faces around the curved surface,
  openEnded = false)  //  if openEnded is true, the ends of the cylinder will not be rendered.
```

**Torus**

-  It is a donut shape

```js
THREE.TorusGeometry(
radius,
tubeWidth = 40, 
radialSegments= 8, 
tubularSegments = 6)
```

**TorusKnot**

-  It is a knot shape, sort of like a pretzel. p and q are integers that affect how many twists are in the knot.  				 			 		

```js
THREE.
  TorusKnotGeometry(
  radius,
  tubeWidth = 40,
  radialSegments,
  tubularSegments, p = 2, q = 3,
  heightScale = 1)
```



### 2D primitive

**Plane**

-  `segments ` parameters subdivide the plane into smaller rectangles

```js
THREE.PlaneGeometry(
width, 
height, 
widthSegments = 1,
heightSegments = 1)
```

**Circle**

-  It is a regular polygon.

```js
THREE.CircleGeometry(radius, numberOfSides = 8)
```

**Ring**

-  It is a circle with a hole in the middle.

```js
THREE.RingGeometry(
innerRadius, 
outerRadius, 
radialSegments = 8,
ringSegments = 8
```

