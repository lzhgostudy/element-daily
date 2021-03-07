<template lang="pug">
  .container
    el-form(:model="form" :rules="rules" ref="form" label-width="100px")
      el-form-item(label="活动名称" prop="name")
        el-input(v-model="form.name")

      el-form-item(label="活动区域" prop="region")
        el-select(v-model="form.region" placeholder="选择活动区域")
          el-option(label="区域一" value="shanghai")
          el-option(label="区域二" value="beijing")

      el-form-item(label="活动时间" required)
        el-col(:span="11")
          el-form-item(prop="date1")
            el-date-picker(type="date" placeholder="选择日期" v-model="form.date1" style='width:100%')
        el-col.line(:span="2") -
        el-col(:span="11")
          el-form-item(prop="date2")
            el-date-picker(placeholder="选择时间" v-model="form.date2" style='width: 100%')
        
      el-form-item(label="即时配送" prop="delivery")
        el-switch(v-model="form.delivery")

      el-form-item(label="活动性质" prop="type")
        el-checkbox-group(v-model="form.type")
          el-checkbox(label="美食" name="type")
          el-checkbox(label="地推活动" name="type")
          el-checkbox(label="线下主题活动" name="type")
          el-checkbox(label="单纯品牌曝光" name="type")

      el-form-item(label="特殊资源" prop="resource")
        el-radio-group(v-model="form.resource")
          el-radio(label="线上品牌商赞助")
          el-radio(label="线下场地免费")

      el-form-item(label="活动形式" prop="desc")
        el-input(type="textarea" v-model="form.desc")
      
      el-form-item
        el-button(type="primary" @click="submitForm('ruleForm')") 立即创建
        el-button(@click="resetForm('ruleForm')") 重置
</template>
<script>
export default {
  data() {
    return {
      rules: {
        name: [
          { required: true,message: '请输入活动名称', trigger: 'blur' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ],
        region: [
          { required: true, message: '请选择活动区域', trigger: 'change' }
        ],
        date1: [
          { type: 'date', required: true, message: '请选择日期', trigger: 'change' }
        ],
        date2: [
          { type: 'date', required: true, message: '请选择时间', trigger: 'change' }
        ],
        type: [
          { type: 'array', required: true, message: '至少选择一个活动性质', trigger: 'change' }
        ],
        resource: [
          { required: true, message: '请选择活动资源', trigger: 'change' }
        ],
        desc: [
          { required: true, message: '请填写活动形式', trigger: 'blur' }
        ]
      },
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: '',
      }
    }
  },
  methods: {
    submitForm() {
      this.$refs.form.validate(valid => {
        if(valid) {
          console.log('submit!');
        }else {
          console.log('error submit!');
          // return false;
        }
      })
    },
    resetForm() {
      this.$refs.form.resetFields()
    }
  }
}
</script>