<template lang="pug">
  .container
    el-form(ref="form" :inline="true" :model="form")
      el-form-item(label="审批人")
        el-input(v-model="form.user" placeholder="审批人")
      
      el-form-item(label="活动区域")
        el-select(v-model="form.region" placeholder="活动区域")
          el-option(label="区域一" value="shanghai")
          el-option(label="区域二" value="beijing")

      el-form-item
        el-button(type="primary" @click="onSubmit") 查询
</template>
<script>
export default {
  data() {
    return {
      form: {
        user: '',
        region: '',
      }
    }
  },
  methods: {
    onSubmit() {

    }
  }
}
</script>
<style lang="scss" scoped>
.container {
  // width: 500px;
  margin: 100px auto 0;
}
</style>