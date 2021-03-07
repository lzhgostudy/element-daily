<template lang="pug">
  .container
    el-form(ref="form" :model="form" label-width="80px")
      el-form-item(label="活动名称")
        el-input(v-model="form.name")

      el-form-item(label="活动区域")
        el-select(v-model="form.region" placeholder="请选择活动区域")
          el-option(label="区域一" value="shanghai")
          el-option(label="区域二" value="beijing")
      
      el-form-item(label="活动时间")
        el-col(:span="11")
          el-date-picker(type="date" placeholder="选择日期" v-model='form.date1' style='width: 100%')
        el-col.line(:span="2") -
        el-col(:span="11")
          el-date-picker(placeholder="请选择时间" v-model="form.date2" style='width:100%')

      el-form-item(label="即时配送")
        el-switch(v-model='form.delivery')

      el-form-item(label="活动性质")
        el-checkbox-group(v-model='form.type')
          el-checkbox(label="美食" name="type")
          el-checkbox(label="地推活动" name="type")
          el-checkbox(label="线下主题活动" name="type")
          el-checkbox(label="单纯品牌曝光" name="type")

      el-form-item(label="特殊资质")
        el-radio-group(v-model="form.resource")
          el-radio(label="线上品牌商赞助")
          el-radio(label="线下场地免费")

      el-form-item(label="活动形式")
        el-input(type="textarea" v-model="form.desc")

      el-form-item
        el-button(type="primary" @click="onSubmit") 立即创建
        el-button 取消
</template>
<script>
export default {
  data() {
    return {
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        type: [],
        resource: '',
        desc: '',
      }
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!')
    }
  }
}
</script>
<style lang="scss" scoped>
.container {
  width: 500px;
  margin: 100px auto 0;
}
.line{
  text-align: center;
  font-size: 20px;
}
</style>