<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>Composition API</h1>
  <input type="text" v-model="lastName">
  <input type="text" v-model="firstName">
  <p>{{ fullName }}</p>
  <h1>v-model test</h1>
  <div class="main">
    <VmodelWorkspace
      class="width-half-screen"
      @display-alert="displayAlert"
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
<script>
import { defineComponent, watch, ref, computed } from 'vue'
import VmodelWorkspace from './components/VmodelWorkspace.vue'
export default defineComponent ({
  name: 'App',
  components: {
    VmodelWorkspace,
  },
  setup() {
    // refs
    const firstName = ref('Yamato')
    const lastName = ref('Tsuda')
    const fullName = computed(() => lastName.value + ' ' + firstName.value )

    const title = ref('初期値')
    const subTitle = ref('初期値')
    const color = ref('#42b983')
    const date = ref('2021-01-01')
    const radioValue = ref('Japan')
    watch(radioValue, (next, prev) => {
      console.log(`radio changed\n${prev} => ${next}`)
    })

    const checkboxArray = ref(['トマト'])
  
    const file = ref({})
    const imgURL = computed(() => {
      if (file.value?.name) {
        return window.URL.createObjectURL(file.value)
      } return ''
    })

    const displayAlert = ({title, subTitle}) => {
      alert(`title: ${title}\nsubTitle: ${subTitle}\n`)
    }

    return {
      title,
      subTitle,
      color,
      date,
      radioValue,
      checkboxArray,
      file,
      firstName,
      lastName,
      fullName,
      imgURL,
      displayAlert
    }
  },
})
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
