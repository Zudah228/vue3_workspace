<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>v-model test</h1>
  <div class="main">
    <VmodelWorkspace
      class="width-half-screen"
      v-model:title="title"
      v-model:subTitle="subTitle"
      v-model:color="color"
      v-model:date="date"
      v-model:radioValue="radioValue"
      v-model:checkbox="checkboxArray"
      v-model:file="file" />
    <div class="width-half-screen">
      <h2>Parent Component</h2>
      <h3>preview</h3>
      <p>Title: {{ title }}</p>
      <p>SubTitle: {{ subTitle }}</p>
      <p :style="{ color: color }">
        Color: {{ color }}
      </p>
      <p>Date: {{ date }}</p>
      <p>Radio: {{ radioValue }}</p>
      <p>Checkbox: {{ checkboxArray }}</p>
      <div>
        <p>File: </p>
        <img :src="imgURL" :style="{ maxHeight: '100px' }">
      </div>
    </div>
  </div>
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
      title: '初期値',
      subTitle: '初期値',
      color: '#42b983',
      date: '2021-01-01',
      radioValue: 'Japan',
      checkboxArray: ['トマト'],
      file: {},
    }
  },
  computed: {
    imgURL() {
      if (this.file.name) {
        return window.URL.createObjectURL(this.file)
      }
      return ''
    },
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
.main {
  display: flex;
  justify-content: center;
}
.width-half-screen {
  width: 50vw;
}
</style>
