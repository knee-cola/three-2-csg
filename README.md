# What's this?
This is a converter which enables conversion of ThreeJS objects into CSG and back (it works both ways).

CSG objects created by this converter can then be manipulated via [@jscad/csg](https://www.npmjs.com/package/@jscad/csg).

This solution is based on  [ThreeCSG.js converter](https://gist.github.com/chandlerprall/1590424) by [Chandler Prall](https://github.com/chandlerprall).

# Example
The following example is based on a [Stack overflow example](https://stackoverflow.com/questions/24716145/create-a-unique-sphere-geometry-from-a-sphere-and-a-cylinder-three-js#24720819) by [4m1r](https://stackoverflow.com/users/2296997/4m1r):
```javascript
import { toCSG, fromCSG } from 'three-2-csg';

//sphere
var sphere = new THREE.SphereGeometry(2,20,20);
var sphereMesh = new THREE.Mesh( sphere, material );
var sphereCSG = toCSG( sphereMesh ); // converting ThreeJS object to CSG

// cyl
var cylinder = new THREE.CylinderGeometry(0.5, 0.5, 5, 32 );
var cylinderMesh = new THREE.Mesh( cylinder, material );
var cylinderCSG = toCSG( cylinderMesh ); // converting ThreeJS object to CSG

//result
var subtractCSG = sphereCSG.subtract( cylinderCSG );
var result = fromCSG(subtractCSG); // converting CSG back into ThreeJS object

result.geometry.computeVertexNormals();

scene.add( result );
```

## Functions

<dl>
<dt><a href="#toCSG">toCSG(three_model)</a> ⇒ <code>CSG_object</code></dt>
<dd><p>Converts a ThreeJS 3D object into a CSG object</p>
</dd>
<dt><a href="#fromCSG">fromCSG(csg_model)</a> ⇒ <code>THREE_Geometry</code></dt>
<dd><p>Converts a 3D object from CSG into regular ThreeJS geometry</p>
</dd>
</dl>

<a name="toCSG"></a>

## toCSG(three_model) ⇒ <code>CSG_object</code>
Converts a ThreeJS 3D object into a CSG object

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| three_model | <code>\*</code> | ThreeJS object which needs to be converted |

<a name="fromCSG"></a>

## fromCSG(csg_model) ⇒ <code>THREE_Geometry</code>
Converts a 3D object from CSG into regular ThreeJS geometry

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| csg_model | <code>\*</code> | = CSG 3D object to be converted |


# License
MIT License, [http://www.opensource.org/licenses/MIT](http://www.opensource.org/licenses/MIT)