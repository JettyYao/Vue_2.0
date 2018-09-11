<template>
    <el-dialog :visible.sync="visible" width="60%"  @close="$emit('update:usersEditor', false);resetForm('posts')" custom-class="UsersEditor">
        <el-form :model="users" ref="users" label-width="100px">
            <el-form-item label="用户昵称" prop="name">
                <el-input v-model="users.name"></el-input>
            </el-form-item>
            <el-form-item label="用户邮箱" prop="email">
                <el-input v-model="users.email"></el-input>
            </el-form-item>
            <el-form-item label="用户自介" prop="desc">
                <el-input type="textarea" v-model="users.desc" :rows="10" class="textareaArea"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button style="background-color:#7da0ff;color:#fff;" @click="submitForm('users')">立即创建</el-button>
                <el-button @click="resetForm('users')">重置</el-button>
            </el-form-item>
        </el-form>
    </el-dialog>
</template>
<script>
export default {
  name: 'UsersEditor',
  props: {
    usersEditor: Boolean
  },
  data () {
      return {
          visible: this.usersEditor,
          users: {
            name: '',
            email: '',
            content: ''
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
    usersEditor () {
        this.visible = this.usersEditor
    }
  }
}
</script>
<style lang="scss">
.UsersEditor{
  border-radius: 4px !important;
  margin-top: 10vh !important;
  .el-dialog__body{
    padding: 35px 45px 25px 10px;
    .el-form{
      padding-top: 20px;
    }
  }
  .el-input--suffix .el-input__inner{
      padding-right: 50px;
  }
  .el-input__suffix{
      right: 15px;
  }
  .el-textarea__inner:focus, .el-input__inner:focus,.el-select .el-input__inner:focus{
    border-color: #dcdfe6 !important;
  }
  .el-select{
      width: 100%;
  }
}
.el-select-dropdown .el-select-dropdown__wrap{
    margin-bottom: 0 !important;
}
.el-select-dropdown.is-multiple .el-select-dropdown__item.selected{
    color: #7da0ff !important;
  }
</style>
