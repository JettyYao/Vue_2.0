<template>
    <el-dialog :visible.sync="visible" width="50%"  @close="$emit('update:personalInfor', false);resetForm('ruleForm')" custom-class="personalInfor">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="用户名称" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
            </el-form-item>
            <el-form-item label="用户邮箱" prop="email">
                <el-input v-model="ruleForm.email"></el-input>
            </el-form-item>
            <el-form-item label="用户资料" prop="desc">
                <el-input type="textarea" v-model="ruleForm.desc" :autosize="{ minRows: 3, maxRows: 7}" class="textareaArea"></el-input>
            </el-form-item>
            <el-form-item label="用户权限" prop="delivery">
                <el-switch v-model="ruleForm.delivery" active-text="赋权为管理员"></el-switch>
            </el-form-item>
            <el-form-item>
                <el-button style="background-color:#7da0ff;color:#fff;" @click="submitForm('ruleForm')">立即创建</el-button>
                <el-button @click="resetForm('ruleForm')">重置</el-button>
            </el-form-item>
        </el-form>
    </el-dialog>
</template>
<script>
export default {
  name: 'personalInfor',
  props: {
    personalInfor: Boolean
  },
  data () {
      return {
          visible: this.personalInfor,
          ruleForm: {
          name: '',
          email: '',
          desc: '',
          delivery: false
        },
        rules: {
          name: [
            { required: true, message: '请输入用户名称', trigger: 'blur' },
            { min: 3, message: '最短长度为3个字符串', trigger: 'blur' }
          ],
          email: [
            { required: true, message: '请输入用户有效邮箱地址', trigger: 'change' },
            { type: 'email', message: '请输入正确的邮箱地址', trigger: ['blur', 'change'] }
          ],
          desc: [
            { required: true, message: '请填写用户个人资料', trigger: 'blur' }
          ]
        }
      }
  },
  methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!')
          } else {
            alert('error submit!!')
            return false
          }
        })
      },
      resetForm(formName) {
        this.$refs[formName].resetFields()
      }
  },
  watch: {
    personalInfor () {
        this.visible = this.personalInfor
    }
  }
}
</script>
<style lang="scss">
.personalInfor{
    padding: 25px 35px 25px 15px;
    // margin-top: 50px !important;
    border-radius: 4px !important;
    background-color: #fefefe;
    .el-switch.is-checked .el-switch__core{
        background-color: #7da0ff;
        border-color: #7da0ff;
    }
    .el-switch__label{
        color: #868688;
    }
    .el-switch__label.is-active{
        color: #7da0ff;
    }
}
</style>
