<template>
    <el-dialog :visible.sync="visible" width="60%"  @close="$emit('update:postsEditor', false);resetForm('posts')" custom-class="PostsEditor">
        <el-form :model="posts" ref="posts" label-width="100px">
            <el-form-item label="内容标题" prop="title">
                <el-input v-model="posts.title"></el-input>
            </el-form-item>
            <el-form-item label="内容标签">
                <el-select v-model="tags" multiple placeholder="请选择">
                    <el-option v-for="item in tagslist" :key="item.value" :label="item.label" :value="item.value">
                    </el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="内容正文" prop="content">
                    <el-input type="textarea" v-model="posts.content" :rows="10" class="textareaArea"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button style="background-color:#7da0ff;color:#fff;" @click="submitForm('posts')">立即创建</el-button>
                <el-button @click="resetForm('posts')">重置</el-button>
            </el-form-item>
        </el-form>
    </el-dialog>
</template>
<script>
export default {
  name: 'PostsEditor',
  props: {
    postsEditor: Boolean
  },
  data () {
      return {
          visible: this.postsEditor,
          posts: {
            title: '',
            tags: [],
            content: ''
          },
          tagslist: [{
           value: '选项1',
           label: '黄金糕'
          }, {
           value: '选项2',
           label: '双皮奶'
          }],
          tags: [],
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
        this.tags = []
      }
  },
  watch: {
    postsEditor () {
        this.visible = this.postsEditor
    }
  }
}
</script>
<style lang="scss">
.PostsEditor{
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
