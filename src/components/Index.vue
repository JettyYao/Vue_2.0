<template>
  <div class="frame">
    <el-row>
      <el-col :span="5" class="dashboard">
        <header>
          <el-row>
            <el-col :span="12" class="logo"><i class="fab fa-soundcloud"></i><strong class="logoName">Cloud</strong></el-col>
            <el-col :span="12" class="messageTip">
              <el-badge is-dot>
                <el-tooltip class="item" effect="dark" content="来信信箱" placement="bottom">
                  <i class="el-icon-bell"></i>
                </el-tooltip>
              </el-badge>
            </el-col>
          </el-row>
        </header>
        <div class="routeLink">
          <el-button><i class="fas fa-envelope"></i>Send Message</el-button>
          <div class="link">
            <ul>
              <router-link tag="li" to="#">
                <i class="el-icon-bell"></i> Every News
                <span class="count">3</span>
              </router-link>
              <router-link tag="li" to="#">
                <i class="el-icon-edit-outline"></i> Each Posts
                <!-- <span class="count">3</span> -->
              </router-link>
              <router-link tag="li" to="#">
                <i class="fas fa-user-secret"></i> Every Users
                <span class="count newTip">new</span>
              </router-link>
              <router-link tag="li" to="#">
                <i class="el-icon-service"></i> Each Comments
                <span class="count">99+</span>
              </router-link>
            </ul>
          </div>
          <div class="aphorism">
            <div><i class="fas fa-dot-circle" style="color: #b9cbff;"></i> Keep Doing</div>
            <div><i class="fas fa-dot-circle" style="color: #ffc8c7;"></i> Pursue Better</div>
            <div><i class="fas fa-circle" style="color: #d3d4d8;"></i> Love All my Love</div>
          </div>
        </div>
        <div class="postNum">
          <div class="progress">
            <el-progress :show-text=false :stroke-width="8" :percentage="80" color="#ffe27a"></el-progress>
            <p><i class="el-icon-upload" style="padding-right: 10px"></i> 1000 articles have been written ...</p>
          </div>
        </div>
      </el-col>
      <el-col :span="19" class="content">
        <div class="NewPart BoxSize">
          <el-row>
            <el-col :span="8" class="ListArea">
              <div class="AreaHeader">
                <ul class="clear">
                  <li>
                    <el-tooltip class="item" effect="dark" content="菜单栏" placement="bottom">
                      <i class="el-icon-menu"></i>
                    </el-tooltip>
                  </li>
                  <li>
                    <el-tooltip class="item" effect="dark" content="搜索" placement="bottom">
                      <i class="el-icon-search"></i>
                    </el-tooltip>
                  </li>
                  <li>
                    <el-tooltip class="item" effect="dark" content="删除" placement="bottom">
                      <i class="el-icon-delete"></i>
                    </el-tooltip>
                  </li>
                </ul>
              </div>
              <div class="ListMenu">
                <div class="tooltip">
                  <i class="fab fa-sellsy"></i> Newest
                </div>
                <div class="ListShow">
                  <el-scrollbar style="height: 100%">
                    <ul>
                      <li style="background-color:#fff">
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#d3d4d8;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle">
                              Monday sharing meeting
                            </div>
                            <div class="eachContent">
                              <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
                              <span class="eachDay">100 days ago</span>
                            </div>
                          </el-col>
                        </el-row>
                      </li>
                      <li>
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#d3d4d8;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle">
                              Monday sharing meeting
                            </div>
                            <div class="eachContent">
                              <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
                              <span class="eachDay">100 days ago</span>
                            </div>
                          </el-col>
                        </el-row>
                      </li>
                      <li>
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#d3d4d8;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle">
                              Monday sharing meeting
                            </div>
                            <div class="eachContent">
                              <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
                              <span class="eachDay">100 days ago</span>
                            </div>
                          </el-col>
                        </el-row>
                      </li>
                      <li>
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#d3d4d8;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle">
                              Monday sharing meeting
                            </div>
                            <div class="eachContent">
                              <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
                              <span class="eachDay">100 days ago</span>
                            </div>
                          </el-col>
                        </el-row>
                      </li>
                    </ul>
                  </el-scrollbar>
                </div>
              </div>
              <div class="addContent">
                <el-button icon="el-icon-plus" circle size="medium"></el-button>
              </div>
            </el-col>
            <el-col :span="16" class="ContentArea">
              <div class="contentHeader">
                <el-dropdown trigger="click">
                  <span class="el-dropdown-link">
                    <i class="el-icon-more"></i>
                  </span>
                  <el-dropdown-menu slot="dropdown">
                    <el-dropdown-item><i class="el-icon-setting"> 配置</i></el-dropdown-item>
                    <el-dropdown-item><i class="el-icon-close"> 退出</i></el-dropdown-item>
                  </el-dropdown-menu>
                </el-dropdown>
              </div>
              <div class="function">
                <i class="el-icon-edit"></i>
                <i class="el-icon-printer"></i>
              </div>
              <div class="contentShow">
                <el-scrollbar style="height:100%">
                  <div class="top">
                    <el-row :gutter=30>
                      <el-col :span="2" class="left-icon">
                        <i class="fas fa-quote-left"></i>
                      </el-col>
                      <el-col :span="22" class="right-content">
                        <p class="time">22TH JULY 2018</p>
                        <h2>Monday sharing meeting</h2>
                        <el-tag size="small" type="info" closable>News (For Monday)</el-tag>
                      </el-col>
                    </el-row>
                  </div>
                  <div class="bottom">
                    <el-row :gutter=30>
                      <el-col :span="2" class="left-icon"></el-col>
                      <el-col :span="22" class="right-content">
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                      </el-col>
                    </el-row>
                  </div>
                </el-scrollbar>
              </div>
            </el-col>
          </el-row>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'Index',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.dashboard{
  position: fixed;
  left: 0;
  top: 0;
  box-shadow: 2px 0 10px #d3d4d8;
  z-index: 99;
  header{
    padding: 10px 35px;
    border-bottom: 2px solid #f1f2f6;
    .logo{
      font-size: 35px;
      color: #668efd;
      .logoName{
        font-size: 18px;
        font-weight: bolder;
        vertical-align: middle;
        padding-left: 3px;
      }
    }
    .messageTip{
      text-align: right;
      line-height: 40px;
      color: #d3d4d8;
      i{
        cursor: pointer;
      }
    }
  }
  .routeLink{
    padding: 40px 35px;
    border-bottom: 4px solid #f1f2f6;
    .el-button{
      width: 100%;
      background-color: #668efd;
      color: #fff;
      padding: 13px 0;
      margin-bottom: 15px;
      i{
        padding-right: 10px;
      }
      &:hover{
        background-color: #668efd81;
      }
    }
    .link{
      ul{
        font-size: 14px;
        color: #868688;
        font-weight: bold;
        li{
          position: relative;
          cursor: pointer;
          padding: 18px 5px;
          i{
            padding-right: 15px;
            color: #d3d4d8;
          }
          &:hover,&:hover i{
            color: #668efd81;
          }
          .count{
            position: absolute;
            right: 5px;
            display: inline;
            border-radius: 7px;
            border: 1px solid #d3d4d8;
            padding: 2px 6px;
            font-size: 11px;
            font-weight: normal;
          }
          .newTip{
            background-color: #668efd;
            color: #fff;
            border: 0;
            padding: 2px 5px;
          }
          &:hover .count{
            border-color: #668efd;
          }
          &:hover .newTip{
            border-color: transparent;
          }
        }
      }
    }
    .aphorism{
      margin-top: 13px;
      div{
        color: #868688;
        font-size: 14px;
        padding: 13px 5px;
        font-weight: bold;
        i{
          padding-right: 15px;
        }
      }
    }
  }
  .postNum{
    height: calc(100% - 551px);
    position: relative;
    cursor: default;
    .progress{
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%);
      width: 80%;
      p{
        font-size: 12px;
        color: #d3d4d8;
        padding-top: 7px;
        padding-left: 3px;
      }
    }
  }
}
.content{
  position: fixed;
  right: 0;
  top: 0;
  .BoxSize{
    height: 100%;
    .ListArea{
      width: 31%;
      background-color: #f5f6fa;
      .AreaHeader{
        padding: 10px 30px;
        border-bottom: 2px solid #f1f2f6;
        ul{
          li{
            float: right;
            line-height: 41px;
            padding-left: 25px;
            color: #d3d4d8;
            i{
              cursor: pointer;
            }
            i.el-icon-menu{
              color: #9cb5fd;
            }
          }
        }
      }
      .ListMenu{
        .tooltip{
          font-weight: bold;
          font-size: 12px;
          color: #d3d4d8;
          padding: 13px 30px;
          i{
            padding-left: 5px;
            padding-right: 11px;
          }
        }
        .ListShow{
          height: 446px;
          ul{
            li{
              padding: 32px 30px;
              font-weight: bold;
              border-bottom: 2px solid #f1f2f6;
              cursor: pointer;
              .tip{
                width: 24px;
                height: 24px;
                border-radius: 50%;
                border: 1px solid #ff6d6a;
                background-color: #ffc8c7;
                line-height: 24px;
                text-align: center;
                font-size: 12px;
                color: #ff6d6a;
              }
              .authorName,.eachContent{
                font-size: 12px;
                color: #d3d4d8;
                line-height: 24px;
              }
              .authorName{
                position: relative;
                i{
                  position: absolute;
                  right: 0;
                  top: 50%;
                  transform: translateY(-50%);
                  cursor: pointer;
                  &:hover{
                    color: #ffc8c7;
                  }
                }
              }
              .eachTitle{
                color: #868688;
                line-height: 22px;
                font-size: 15px;
                overflow: hidden;
                text-overflow:ellipsis;
                white-space: nowrap;
              }
              .eachContent{
                position: relative;
                line-height: 20px;
                p{
                  width: 59%;
                  overflow: hidden;
                  text-overflow:ellipsis;
                  white-space: nowrap;
                }
                span{
                  position: absolute;
                  right: 0;
                  top: 0;
                }
              }
            }
          }
        }
      }
      .addContent{
        height: calc(100% - 551px);
        position: relative;
        .el-button{
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%,-50%);
          background-color: #668efd;
          color: #fff;
          &:hover{
            background-color: #668efd81;
          }
        }
      }
    }
    .ContentArea{
      width: 69%;
      .contentHeader{
        padding: 10px 35px;
        line-height: 41px;
        text-align: right;
        border-bottom: 2px solid #f1f2f6;
        .el-dropdown{
          color: #d3d4d8;
          line-height: 1;
          i{
            cursor: pointer;
            color: #d3d4d8;
            font-size: 14px;
            &:hover{
              color: #9cb5fd;
            }
          }
        }
      }
      .function{
        padding: 25px 35px 5px;
        color: #d3d4d8;
        text-align: right;
        i{
          padding: 0 0 0 20px;
          cursor: pointer;
          font-size: 16px;
          &:hover{
            color: #9cb5fd;
          }
        }
      }
      .contentShow{
        height: calc(100% - 153px);
        .top{
          padding: 10px 35px 20px;
          .left-icon{
            text-align: right;
            padding-top: 26px;
            i{
              font-size: 20px;
              color: #9cb5fd;
            }
          }
          .right-content{
            p.time{
              font-size: 12px;
              color: #d3d4d8;
              letter-spacing: 1.5px;
            }
            h2{
              padding: 6px 0;
              font-size: 32px;
              color: #868688;
            }
            .el-tag{
              background-color: #fff;
              border-color: #d3d4d8;
              color: #8e8f92;
              padding: 3px 15px;
              line-height: 17px;
            }
          }
        }
        .bottom{
          padding: 10px 30px 20px;
          .left-icon{
            padding-top: 26px;
          }
          .right-content{
            p{
              padding-right: 25px;
              font-size: 15px;
              color: #868688;
            }
          }
        }
      }
    }
  }
}
</style>
<style lang="scss">
.messageTip{
  .el-badge__content.is-fixed.is-dot{
    top: 11px;
    right: 6px;
    background-color: #668efd !important;
  }
}
.el-dropdown-menu{
  top: 30px !important;
  left: 1246px !important;
  .el-dropdown-menu__item{
    color: #868688;
  }
}
.el-tag .el-icon-close{
  top: 0 !important;
}
</style>

