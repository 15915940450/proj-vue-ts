<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue';


let result = import.meta.env;
console.log('result', result);
console.log('import.meta\u200b.env');
// {BASE_URL: '/', MODE: 'development', DEV: true,  PROD: false, SSR: false}
// {BASE_URL: '/', MODE: 'production',  DEV: false, PROD: true}

/* 
mode

Env Loading Priorities
An env file for a specific mode (e.g. .env.production) will take higher priority than a generic one (e.g. .env).
*/
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="http://127.0.0.1:8888/" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
