<script lang="ts" setup>
import {onMounted} from 'vue'
import * as THREE from 'three'
// console.log(THREE.REVISION)


let runTHREE=()=>{
  /* 
  要素：
  camera++++++++
  */
  let aspect = (window.innerWidth * .8)/ (window.innerHeight * .4)
  const camera=new THREE.PerspectiveCamera(70,aspect,1e-2,1e2)
  camera.position.z=1
  const scene=new THREE.Scene()
  let size=.4
  const geometry=new THREE.BoxGeometry(size,size,size)
  const material=new THREE.MeshNormalMaterial()
  const mesh=new THREE.Mesh(geometry,material)
  scene.add(mesh)


  const renderer=new THREE.WebGLRenderer({
    antialias:true,
  })
  renderer.setSize(window.innerWidth*.8,window.innerHeight*.4)
  renderer.setAnimationLoop(animation)

  elTHREE.appendChild(renderer.domElement)



  function animation(time:number){
    mesh.rotation.x=time/2000
    mesh.rotation.y=time/1000
    renderer.render(scene,camera)
  }
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


Vite does provide built-in support for .scss, .sass, .less, .styl and .stylus files. There is no need to install Vite-specific plugins for them, but the corresponding pre-processor itself must be installed:
# .scss and .sass
npm add -D sass
<style lang="scss">
.App{
  border: 1px solid dimgray;
}
</style>