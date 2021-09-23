<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>v-model test</h1>
  <VmodelWorkspace
    v-model:title="title"
    v-model:subTitle="subTitle"
    v-model:color="color" />
  <h3>Parent Component</h3>
  <p>title: {{ title }}</p>
  <p>subTitle: {{ subTitle }}</p>
  <p :style="{ color: color }">
    color: {{ color }}
  </p>
  <p>Radio: {{ radioValue }}</p>
  <p>Checkbox: {{ checkboxArray }}</p>
</template>
<script lang="js">
import VmodelWorkspace from './components/VmodelWorkspace.vue'
export default {
  name: 'App',
  components: {
    VmodelWorkspace,
  },
  data() {
    return {
      title: '',
      subTitle: '',
      color: '#000000',
      radioValue: '',
      checkboxArray: [],
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  justify-content: center;
  color: #2c3e50;
  margin-top: 60px;
  margin-bottom: 120px;
}
</style>
