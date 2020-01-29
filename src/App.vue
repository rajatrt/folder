<template>
  <div id="app">
    <h1>Folders</h1>
    <folder v-for="(fold,index) in mockData" :key="fold" :fold="fold" :index="index" :depth="0"/>
  </div>
</template>

<script>
import Folder from './components/folder.vue'
import { mockData } from './mockData.js'

export default {
  name: 'app',
  data(){
    return {
      mockData,
    }
  },
  components: {
    'folder': Folder
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
