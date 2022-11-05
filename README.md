# Vue 3 + TypeScript + Vite

[modes](https://vitejs.dev/guide/env-and-mode.html#modes)
```
vite build --mode staging

# .env.staging
NODE_ENV=production
VITE_APP_TITLE=My App (staging)
```

###### refer

+ [script setup](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup)

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)

## Type Support For `.vue` Imports in TS

Since TypeScript cannot handle type information for `.vue` imports, they are shimmed to be a generic Vue component type by default. In most cases this is fine if you don't really care about component prop types outside of templates. However, if you wish to get actual prop types in `.vue` imports (for example to get props validation when using manual `h(...)` calls), you can enable Volar's Take Over mode by following these steps:

1. Run `Extensions: Show Built-in Extensions` from VS Code's command palette, look for `TypeScript and JavaScript Language Features`, then right click and select `Disable (Workspace)`. By default, Take Over mode will enable itself if the default TypeScript extension is disabled.
2. Reload the VS Code window by running `Developer: Reload Window` from the command palette.

You can learn more about Take Over mode [here](https://github.com/johnsoncodehk/volar/discussions/471).


===t1
```
import {onMounted} from 'vue'
import * as THREE from 'three'
// console.log(THREE.REVISION)


let runTHREE=()=>{
  /* 
  要素：
  camera+scene+geometry+material+mesh+renderer

  renderer=scene+camera
  scene=mesh+...
  mesh=geometry+material
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
```


Path2D()
```
import {onMounted} from 'vue'

onMounted(()=>{
  let ctx=canvasMain.getContext('2d')
  console.log(ctx)


  ctx.save()
  let d_SVGpath ='M11 4C11 1.79086 9.20914 0 7 0H0V48H7C9.20914 48 11 46.2091 11 44L11 4Z'
  let thePath2D_1 = new Path2D(d_SVGpath)
  ctx.fillStyle ='#FFBB00'
  ctx.fill(thePath2D_1)

  let thePath2D_2 = new Path2D('M5.5 30V17')
  ctx.strokeStyle='white'
  ctx.lineWidth=2
  ctx.lineCap ='round'
  ctx.lineJoin ='round'
  ctx.stroke(thePath2D_2)
  ctx.restore()
})
```