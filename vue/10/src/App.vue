<!--组件的模板结构-->
<template>
  <div>
    <h2 @click="changeMsg">App.vue...{{ msg }}</h2>
  </div>
</template>

<!--组件的js代码-->
<script>
// 以后在这里面写vue的配置内容
export default {
  data () {
    return {
      msg: 'hello'
    }
  },
  methods: {
    changeMsg () {
      this.msg = 'world'
    }
  }
}
</script>

<!--组件的css样式-->
<style lang="scss">

</style>
