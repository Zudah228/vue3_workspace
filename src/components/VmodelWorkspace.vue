<template>
  <div class="hello">
    <h3>Child Component</h3>
    <div class="text-form">
      <p>title: </p>
      <input
        type="text"
        class="input-text"
        :value="title"
        @input="changeTitle($event.target.value)">
    </div>
    <div class="text-form">
      <p>subTitle: </p>
      <input
        type="text"
        class="input-text"
        :value="subTitle"
        @input="changeSubTitle($event.target.value)">
    </div>
    <input
      type="color"
      :value="color"
      @input="changeColor($event.target.value)">
      <!-- TODO: DatePick Input -->
      <!-- TODO: Checkbox Input -->
      <!-- TODO: Radio Input -->
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
  },
  emits: ['update:title', 'update:subTitle'],
  methods: {
    changeTitle(title) {
      this.$emit('update:title', title) // previously was `this.$emit('input', title)`
    },
    changeSubTitle(subTitle) {
      this.$emit('update:subTitle', subTitle) // previously was `this.$emit('input', title)`
    },
    changeColor(color) {
      this.$emit('update:color', color) // previously was `this.$emit('input', title)`
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: block;
  border-bottom: solid;
  padding-bottom: 40px;
  border-color: #42b983;
}
.input-text {
  height: min-content;
  margin: 18px;
}
.text-form {
  display: flex;
  flex-flow: row;
  justify-content: center;
  text-align: center;
}
</style>
