<template>
  <div class="hello">
    <h2>Child Component</h2>
    <h3>Input</h3>

    <!-- Title Input -->
    <div class="text-form">
      <p>title: </p>
      <input
        type="text"
        class="text-input"
        @input="changeTitle($event.target.value)">
    </div>
    <div class="text-form">

    <!-- SubTitle Input -->
      <p>subTitle: </p>
      <input
        type="text"
        class="text-input"
        @input="changeSubTitle($event.target.value)">
    </div>

    <!-- Color Input -->
    <div class="text-form">
      <p>color: </p>
      <input
        type="color"
        :value="color"
        @input="changeColor($event.target.value)">
      </div>

    <!-- Date Input -->
    <div class="text-form">
      <p>date: </p>
      <input
        type="date"
        :value="date"
        @input="changeDate($event.target.value)">
    </div>

    <!-- Radio Input -->
    <div class="text-form">
      <p>radio: </p>
      <div v-for="(country, i) in countries" :key="i">
        <input
          type="radio"
          name="radio"
          :id="country"
          :value="country"
          @input="changeRadioValue($event.target.value)" >
        <label :for="country">{{ country }}</label>
      </div>
    </div>

    <!-- Checkbox Input -->
    <div class="text-form">
      <p>checkbox: </p>
      <div v-for="(tomato, i) in tomatoes" :key="i">
        <input
          v-model="model"
          type="checkbox"
          name="checkbox"
          :id="tomato"
          :value="tomato"
          @change="changeCheckbox()" >
        <label :for="tomato">{{ tomato }}</label>
      </div>
    </div>

    <!-- File Inout -->
    <div class="text-form">
      <p>file: </p>
      <input type="file" @input="changeFile($event.target.files[0])">
    </div>

  </div>
</template>
<script>
export default {
  name: 'VmodelWorkspace',
  props: {
    // TODO: 初期値の設定をする
    // TODO: 非同期で初期値を取得する
    title: String,
    subTitle: String,
    color: String,
    date: String,
    radioValue: String,
    file: File,
  },
  emits: [
    'update:title',
    'update:subTitle',
    'update:color',
    'update:date',
    'update:radioValue',
    'update:checkbox',
    'update:file',
  ],
  data() {
    return {
      countries: ['Japan', 'USA', 'China'],
      tomatoes: ['トマト', 'プチトマト', 'ホールトマト缶', 'カットトマト缶'],
      model: [],
    }
  },
  methods: {
    changeTitle(title) {
      this.$emit('update:title', title) 
    },
    changeSubTitle(subTitle) {
      this.$emit('update:subTitle', subTitle)
    },
    changeColor(color) {
      this.$emit('update:color', color)
    },
    changeDate(date) {
      this.$emit('update:date', date)
    },
    changeRadioValue(value) {
      this.$emit('update:radioValue', value)
    },
    changeCheckbox() {
      this.$emit('update:checkbox', this.model)
    },
    changeFile(file) {
      this.$emit('update:file', file)
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: flex;
  flex-flow: column;
  justify-content: center;
  border-right: solid;
  padding-bottom: 40px;
  border-color: #42b983;
}
input {
  justify-content: center;
  text-align: center;
  margin: 10px;
}
.text-input {
  height: min-content;
  padding: 4px;
  text-align: start;
}
.text-form {
  display: flex;
  flex-flow: row;
  vertical-align: center;
  align-items: center;
  justify-content: center;
  text-align: center;
}
</style>
