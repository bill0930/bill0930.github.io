### Hello, Three.js

### World of Three.js

[Github Link](https://github.com/mrdoob/three.js)

[Three.js Demos](http://threejs.org/)

[Documentation](http://threejs.org/docs/)

Three.js

-  Use WebGL. a Javascript API for rendering graphics without plugins, which based on OpenGL
-  Supports rendering with HTML5 Canvas API and Scalable Vector Graphcis



### Example Coding

-  Get a spinning shape rendering in the browser

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<style>
			body {
				background-color: #ffffff;
				margin: 0;
				overflow: hidden;
			}
		</style>
	</head>
	<body>
		<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/94/three.min.js"></script>
		<script>

			var camera, scene, renderer;
			var geometry, material, mesh;

			function init() {

				camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 10 );
				camera.position.z = 3;

				scene = new THREE.Scene();
				scene.background = new THREE.Color( 0xffffff );

				geometry = new THREE.SphereGeometry( 1 );
				material = new THREE.MeshBasicMaterial( { color: 0x000000, wireframe: true } );

				mesh = new THREE.Mesh( geometry, material );
				scene.add( mesh );

				renderer = new THREE.WebGLRenderer( { antialias: true } );
				renderer.setSize( window.innerWidth, window.innerHeight );
				document.body.appendChild( renderer.domElement );				
				
			}

			function animate( time ) {

				mesh.rotation.x = time * 0.0005;
				mesh.rotation.y = time * 0.001;

				renderer.render( scene, camera );
				requestAnimationFrame( animate );

			}
			init();
			requestAnimationFrame( animate );

		</script>
	</body>
</html>
```



### Declaring objects

```js
var camera, scene, renderer;
var geometry, material, mesh;
```

```js
scene = new THREE.Scene();
```


| Elements | Description                                                  |
| -------- | ------------------------------------------------------------ |
| Scene    | a list of objects that affect what is displayed on the screen(such as 3D models and lights) |
| Mesh     | can be displayed in a `scene`, consists of `geometry`, `material` |
| Geometry | the object shape                                             |
| Material | a `color` ,`image` or other texture that defines hwo the faces of the shape appear |

```js
geometry = new THREE.IcosahedronGeometry(200, 1);
material = new THREE.MeshBasicMaterial({ color: 0x000000, wireframe:
   true, wireframeLinewidth: 2 });
mesh = new THREE.Mesh(geometry, material);
```

```js
scene.add(mesh); // push the mesh that consists of geomotry and metrial into the scene
```

### Renderers

-  take the objects in a scene
-  perform some calculations
-  ask the browser to display the result in a specific format like WebGL
-  creates a new <canvas> element by default that should be added to the DOM



```js
renderer = new THREE.CanvasRenderer();
renderer.setSize(window.innerWidth, widow.innerHeight);
document.body.appendChild(renderer.domElement);
```

-  Use `CanvasRenderer` as our method of displaying the scene.
-  telling renderers to display the scene at the full size of the browser window with our `setSize( )` call.
-  add the renderer's canvas to the DOM with  `appendChild(renderer.domElement).`



```javascript
camera = new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,1,1000);
camera.position.z = 500;

```

-  `PerspectiveCamera` Instance displays thw rold from a single point in space.
-  Creates a little bit of distortion due to distance(objects that are farther away appear smaller)



-  `OrthographicCamera` class
   -  loooking out from a place
   -  someitmes used for **isometric**(2.5D) games and level editors
-  `PerspectiveCamera`objects parametres
   -  `field of view (in degree` ), control how wide the camera lens is 
   -  `aspect ratio` , the ratio of the canvas's width to its height
   -  `near-lance frustum`, ,the closest an object can be to the camera and still be
      seen 
   -  `far-plane frustum`, the farthest an object can be from the camera and still
      be rendered

![perspectve_and_orthographic](https://i.imgur.com/lT1ReoX.png)



Three.js uses **spatial coordinate system**

-  the x-axis increases from left to right  
-  the z-axis increase from back to front
-  the y-axis increases upward

Most objects have a *position* and *scale*

-  both of which are repsented by a three.dimensional vector(specifically `THREE.Vector3` )
-  `Rotation` are represented by a `THREE.Euler` instance, which is an abstration that allows treating rotaion much like a vector.

All objects are initialized at the position (0,0,0) , called **origin** . 

Rotation starts at (0,0,0) and scale at (1,1,1)

```js
 renderer.render(scene, camera);
```

-   display the scene by asking the renderer to display it from the camera's perspective



render loop 

```js
 animate();
 
   function animate() {
     requestAnimationFrame(animate);
     mesh.rotation.x = Date.now() * 0.00005;
     mesh.rotation.y = Date.now() * 0.0001;
     renderer.render(scene, camera);
   }
```

-  `requestAnimationFrame()` executes the function passed to it when the browser is ready to paint a new frame.

-  perform any neccesary updates to the scene 
-  changed the mesh's rotation vector



### Choosing environment

-  use Google Chrome Canary
-  has advantages for 
   -  advanced performance profiling
   -  the ability to emulate touch events
   -  support for inpsecting canvas frames.
   -  **about:flags**
   -  **Chrome Developer Tools settings**

-  Has script-editing environment that works well
-  **Chrome Developer Tools** —> **Sources**—>
   -  configure Chrome to edit files from your local filesystem
   -   syntax highlighting, debugging, autocompletion, source
      mapping for minified files, revision control that visually shows changes, and the ability to run the code instantly without reloading the page

**Some Docoumentation** 

[MeshBasicMaterial](https://threejs.org/docs/#api/en/materials/MeshBasicMaterial)

[IcosahedronGeometry](https://threejs.org/docs/#api/en/geometries/IcosahedronGeometry)

