<template lang="pug">
  .container
    el-radio-group(v-model="labelPosition" size="small")
      el-radio-button(label="left") 左对齐
      el-radio-button(label="right") 右对齐
      el-radio-button(label="top") 顶部对齐

    el-form(:label-position="labelPosition" label-width="80px" :model="form")
      el-form-item(label="名称")
        el-input(v-model="form.name")
      
      el-form-item(label="活动区域")
        el-input(v-model="form.region")

      el-form-item(label="活动形式")
        el-input(v-model="form.type")
</template>
<script>
export default {
  data() {
    return {
      labelPosition: 'left',
      form: {
        name: '',
        region: '',
        type: '',
      }
    }
  },
  methods: {

  }
}
</script>