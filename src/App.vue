<script lang="ts" setup>
import {onMounted} from 'vue'
import * as _3D from 'three'


  /* 
  要素：
  camera+scene+geometry+material+mesh+object3d+group+renderer

  renderer=scene+camera
  scene=mesh+object3d+group...
  mesh=geometry+material
  */
let runTHREE=()=>{
  let w=800;
  let h=600;
  let renderer = new _3D.WebGLRenderer({
    antialias:true,
  })
  renderer.setSize(w,h)

  let scene=new _3D.Scene()

  let size=0.8
  let geometry = new _3D.BoxGeometry(size, size, size)
  let material=new _3D.MeshNormalMaterial()
  let mesh=new _3D.Mesh(geometry,material)

  let object3d=new _3D.Object3D()
  object3d.add(mesh)


  /* 
  import { Object3D } from '../core/Object3D.js';

  class Group extends Object3D {

    constructor() {

      super();

      this.isGroup = true;

      this.type = 'Group';

    }

  }

  export { Group };
  */
  let group=new _3D.Group()
  group.add(object3d)
  scene.add(group)

  let aspect=w/h
  let camera=new _3D.PerspectiveCamera(75,aspect,1e-2,1e2)
  camera.position.z=1
  camera.position.x=1
  camera.lookAt(0,0,0)

  let animation = (msec:number) => { 
    // camera.position.x += .001
    mesh.rotation.x+=Math.random()*1e-2
    mesh.rotation.y += Math.random() * 1e-2
    mesh.rotation.z += Math.random() * 1e-2

    mesh.position.x = Math.random() * 1e-1
    mesh.position.y = Math.random() * 1e-1
    mesh.position.z = Math.random() * 1e-1
    renderer.render(scene, camera)
  }
  renderer.setAnimationLoop(animation)


  


  elTHREE.appendChild(renderer.domElement)
}
onMounted(()=>{
  runTHREE()
})
</script>
<template>
<div class="App">
  <h1>Hello Cube!</h1>
  <div id="elTHREE">
    <!-- <canvas id="canvasMain"></canvas> -->
  </div>
</div>
</template>


Vite does provide built-in support for .scss, .sass, .less, .styl and .stylus files. 
There is no need to install Vite-specific plugins for them, 
but the corresponding pre-processor itself must be installed:
  # .scss and .sass
  npm add -D sass
<style lang="scss">
.App{
  border: 10px solid dimgray;
}

</style>