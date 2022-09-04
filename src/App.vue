<template>
  <div id="app">
    <button @click="loading_1 = !loading_1">디스플레이1ON/OFF</button>
    <button @click="loading_2 = !loading_2">디스플레이2ON/OFF</button>
    <HelloWorld v-if="loading_1" msg="Welcom to vue-vis-network"/>
    <drag-drop v-if="loading_2" msg="Welcom to vue-drag-drop"></drag-drop>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import DragDrop from './components/DragDrop.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    DragDrop
  },
  data() {
    return {
      loading_1: false,
      loading_2: false
    }
  }
}
</script>

<style>
</style>
