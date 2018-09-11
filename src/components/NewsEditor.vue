<template>
    <el-dialog :visible.sync="visible" width="60%"  @close="$emit('update:newsEditor', false);resetForm('news')" custom-class="NewsEditor">
        <el-form :model="news" ref="news" label-width="100px">
            <el-form-item label="新闻标题" prop="name">
                <el-input v-model="news.name"></el-input>
            </el-form-item>
            <el-form-item label="新闻内容" prop="desc">
                <el-input type="textarea" v-model="news.desc" :rows="10" class="textareaArea"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button style="background-color:#7da0ff;color:#fff;" @click="submitForm('news')">立即创建</el-button>
                <el-button @click="resetForm('news')">重置</el-button>
            </el-form-item>
        </el-form>
    </el-dialog>
</template>
<script>
export default {
  name: 'NewsEditor',
  props: {
    newsEditor: Boolean
  },
  data () {
      return {
          visible: this.newsEditor,
          news: {
            name: '',
            desc: ''
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
    newsEditor () {
        this.visible = this.newsEditor
    }
  }
}
</script>
<style lang="scss">
.NewsEditor{
  border-radius: 4px !important;
  .el-dialog__body{
    padding: 35px 45px 25px 10px;
    .el-form{
      padding-top: 20px;
    }
  }
  .el-textarea__inner:focus, .el-input__inner:focus{
    border-color: #dcdfe6;
  }
}
</style>
