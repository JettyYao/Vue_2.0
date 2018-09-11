<template>
  <el-dialog :visible.sync="visible" width="70%"  @close="$emit('update:messageBox', false)" custom-class="messageBox">
    <div class="BoxTop">
        <el-row>
            <el-col :span="16">
                <el-row>
                    <el-col :span="6" class="DataTip">EmailBox</el-col>
                    <el-col :span="18">
                        <el-date-picker v-model="data" type="daterange" align="right" unlink-panels range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期" :picker-options="pickerOptions"  format="yyyy 年 MM 月 dd 日" prefix-icon="el-icon-search">
                        </el-date-picker>
                    </el-col>
                </el-row>
            </el-col>
            <el-col :span="8">
                <el-tooltip class="item" effect="dark" content="Only Show Unread" placement="top">
                    <el-switch v-model="isReadButton" active-color="#668efd"></el-switch>
                </el-tooltip>
            </el-col>
        </el-row>
    </div>
    <div class="BoxContent">
        <el-scrollbar style="height:100%">
            <el-collapse v-model="activeType" accordion>
                <el-collapse-item title="每日邮件 DaysEmails" name="1">
                    <ul class="ContentList">
                        <li v-for="(item,index) in EmailDatas" :key="index">
                            <el-popover placement="bottom" width="284" trigger="click">
                            <div>
                                <p>
                                    <el-row>
                                        <el-col :span="5">From：</el-col>
                                        <el-col :span="19">{{item.username}}</el-col>
                                    </el-row>
                                </p>
                                <p>
                                    <el-row>
                                        <el-col :span="5">Mails：</el-col>
                                        <el-col :span="19" class="overhidden">{{item.email}}</el-col>
                                    </el-row>
                                </p>
                                <p>
                                    <el-row>
                                        <el-col :span="5">Cons：</el-col>
                                        <el-col :span="19">{{item.content}}</el-col>
                                    </el-row>
                                </p>
                            </div>
                            <div slot="reference">
                                <el-row>
                                    <el-col :span="4" style="text-align:center"><i :class="[item.isread ? 'el-icon-success' : 'el-icon-info']"></i></el-col>
                                    <el-col :span="20" class="overhidden">From：{{item.username}}</el-col>
                                </el-row>
                            </div>
                            </el-popover>
                        </li>
                    </ul>
                </el-collapse-item>
                <el-collapse-item title="每周邮件 WeeksEmails" name="2">
                    <ul class="ContentList">
                        <li v-for="(item,index) in EmailDatas" :key="index">
                            <el-popover placement="bottom" width="284" trigger="click">
                            <div>
                                <p>
                                    <el-row>
                                        <el-col :span="5">From：</el-col>
                                        <el-col :span="19">{{item.username}}</el-col>
                                    </el-row>
                                </p>
                                <p>
                                    <el-row>
                                        <el-col :span="5">Email：</el-col>
                                        <el-col :span="19" class="overhidden">{{item.email}}</el-col>
                                    </el-row>
                                </p>
                                <p>{{item.content}}</p>
                            </div>
                            <div slot="reference">
                                <el-row>
                                    <el-col :span="4" style="text-align:center"><i :class="[item.isread ? 'el-icon-success' : 'el-icon-info']"></i></el-col>
                                    <el-col :span="20" class="overhidden">From：{{item.username}}</el-col>
                                </el-row>
                            </div>
                            </el-popover>
                        </li>
                    </ul>
                </el-collapse-item>
                <el-collapse-item title="每月邮件 MonthEmails" name="3">
                    <ul class="ContentList">
                        <li v-for="(item,index) in EmailDatas" :key="index">
                            <el-popover placement="bottom" width="284" trigger="click">
                            <div>
                                <p>
                                    <el-row>
                                        <el-col :span="5">From：</el-col>
                                        <el-col :span="19">{{item.username}}</el-col>
                                    </el-row>
                                </p>
                                <p>
                                    <el-row>
                                        <el-col :span="5">Email：</el-col>
                                        <el-col :span="19" class="overhidden">{{item.email}}</el-col>
                                    </el-row>
                                </p>
                                <p>{{item.content}}</p>
                            </div>
                            <div slot="reference">
                                <el-row>
                                    <el-col :span="4" style="text-align:center"><i :class="[item.isread ? 'el-icon-success' : 'el-icon-info']"></i></el-col>
                                    <el-col :span="20" class="overhidden">From：{{item.username}}</el-col>
                                </el-row>
                            </div>
                            </el-popover>
                        </li>
                    </ul>
                </el-collapse-item>
                <el-collapse-item title="年度邮件 YearsEmails" name="4">
                    <ul class="ContentList">
                        <li v-for="(item,index) in EmailDatas" :key="index">
                            <el-popover placement="bottom" width="284" trigger="click">
                            <div>
                                <p>
                                    <el-row>
                                        <el-col :span="5">From：</el-col>
                                        <el-col :span="19">{{item.username}}</el-col>
                                    </el-row>
                                </p>
                                <p>
                                    <el-row>
                                        <el-col :span="5">Email：</el-col>
                                        <el-col :span="19" class="overhidden">{{item.email}}</el-col>
                                    </el-row>
                                </p>
                                <p>{{item.content}}</p>
                            </div>
                            <div slot="reference">
                                <el-row>
                                    <el-col :span="4" style="text-align:center"><i :class="[item.isread ? 'el-icon-success' : 'el-icon-info']"></i></el-col>
                                    <el-col :span="20" class="overhidden">From：{{item.username}}</el-col>
                                </el-row>
                            </div>
                            </el-popover>
                        </li>
                    </ul>
                </el-collapse-item>
            </el-collapse>
        </el-scrollbar>
    </div>
  </el-dialog>
</template>
<script>
export default {
  name: 'messageBox',
  props: {
    messageBox: Boolean
  },
  data () {
      return {
        visible: this.messageBox,
        data: '',
        MailDatas: ['1','2','3','4','5','6','7'],
        isReadButton: 'false',
        activeType: ['1'],
        pickerOptions: {
            shortcuts: [{
                text: '一周内邮件',
                onClick(picker) {
                const end = new Date();
                const start = new Date();
                start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
                picker.$emit('pick', [start, end]);
                }
            }, {
                text: '一月内邮件',
                onClick(picker) {
                const end = new Date();
                const start = new Date();
                start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
                picker.$emit('pick', [start, end]);
                }
            }, {
                text: '三月内邮件',
                onClick(picker) {
                const end = new Date();
                const start = new Date();
                start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
                picker.$emit('pick', [start, end]);
                }
            }]
        },
        EmailDatas: [{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...this is a test...this is a test...this is a test...this is a test...',isread: false},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: false},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: false},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true},{username: 'Jetty Smith',email: 'yao1508728331@gmail.com',content: 'this is a test...',isread: true}]
      }
  },
  methods: {
  },
  watch: {
    messageBox () {
        this.visible = this.messageBox
    }
  }
}
</script>
<style lang="scss" scoped>
.BoxTop{
    .DataTip{
        color: #668efd;
        text-align: center;
        font-weight: bold;
        text-transform: uppercase;
        font-size: 22px;
        padding-top: 4px;
    }
    .el-switch{
        height: 30px;
        margin-left: 243px;
    }
}
.BoxContent{
    height: calc(100% - 30px);
    padding:  30px 10px 0 20px;
    .ContentList{
        li{
            display: inline-block;
            cursor: pointer;
            width: 32%;
            margin: 0 1% 5px 0;
            padding: 5px 10px;
            border: 1px solid #e0e0e0;
            border-radius: 3px;
            i.el-icon-success{
                color: #7da0ff;
            }
            i.el-icon-info{
                color: #ffc8c7;
            }
        }
    }
}
</style>
<style lang="scss">
.el-dialog__header{
    display: none;
}
.messageBox{
    background: #fefefe !important;
    height: 80%;
    margin-top: 10vh !important;
    border-radius: 4px !important;
    .BoxTop{
        .el-range-editor.el-input__inner{
            border-radius: 15px;
            height: 30px;
        }
        .el-date-editor .el-range-input, .el-date-editor .el-range-separator{
            color: #8e8f92;
            font-size: 12px;
            line-height: 22px;
        }
        .el-date-editor .el-range__icon,.el-date-editor .el-range__close-icon{
            font-size: 12px;
            line-height: 22px;
        }
        .el-switch__input:focus~.el-switch__core{
            outline: none;
        }
    }
    .el-scrollbar__view{
        padding-right: 10px;
    }
}
.el-dialog__body{
    height: 100%;
}
.el-date-range-picker.has-sidebar{
    left: 130px !important;
}
.el-date-table td.today span, .el-picker-panel__shortcut:hover{
    color: #7da0ff !important;
}
.el-picker-panel [slot=sidebar], .el-picker-panel__sidebar{
    width: auto !important;
    padding: 20px !important;
    .el-picker-panel__shortcut{
        padding: 5px 10px;
    }
}
.el-picker-panel [slot=sidebar]+.el-picker-panel__body, .el-picker-panel__sidebar+.el-picker-panel__body{
    margin-left: 131px !important;
}
.el-date-editor .el-range-separator{
    width: auto !important;
}
</style>
