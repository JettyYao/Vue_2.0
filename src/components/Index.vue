<template>
  <div class="frame">
    <el-row>
      <el-col :span="5" class="dashboard">
        <header>
          <el-row>
            <el-col :span="16" class="logo"><i class="fas fa-archway"></i><strong class="logoName">Horizon</strong></el-col>
            <el-col :span="8" class="messageTip">
              <el-badge is-dot>
                <el-tooltip class="item" effect="dark" content="来信信箱" placement="bottom">
                  <i class="el-icon-bell" @click="messageBox=true"></i>
                </el-tooltip>
              </el-badge>
            </el-col>
          </el-row>
        </header>
        <div class="routeLink">
          <el-button @click="personalInfor=true"><i class="fas fa-crop"></i>Personal information</el-button>
          <div class="link">
            <ul>
              <li @click="changeSelectStatus(0)" :class="{selectLink : 0 == LinkChange}">
                <i class="el-icon-picture-outline"></i> Every News
                <span class="count">3</span>
              </li>
              <li @click="changeSelectStatus(1)" :class="{selectLink : 1 == LinkChange}">
                <i class="el-icon-edit-outline"></i> Each Posts
              </li>
              <li @click="changeSelectStatus(2)" :class="{selectLink : 2 == LinkChange}">
                <i class="fas fa-user-secret"></i> Every Users
                <span class="count newTip">new</span>
              </li>
              <li @click="changeSelectStatus(3)" :class="{selectLink : 3 == LinkChange}">
                <i class="el-icon-service"></i> Each Comments
                <span class="count">99+</span>
              </li>
            </ul>
          </div>
          <div class="aphorism">
            <div><i class="fas fa-dot-circle" style="color: #b9cbff;"></i> Keep Doing</div>
            <div><i class="fas fa-dot-circle" style="color: #ffc8c7;"></i> Pursue Better</div>
            <div><i class="fas fa-circle" style="color: #c3c3c3;"></i> Love All my Love</div>
          </div>
        </div>
        <div class="postNum">
          <div class="progress">
            <el-progress :show-text=false :stroke-width="8" :percentage="80" color="#dadada"></el-progress>
            <p><i class="el-icon-upload" style="padding-right: 10px"></i> 1000 articles have been written ...</p>
          </div>
        </div>
      </el-col>
      <el-col :span="19" class="content">
        <div class="NewPart BoxSize PositionChange" :style="Top">
          <el-row>
            <el-col :span="8" class="ListArea">
              <div class="AreaHeader">
                <ul class="clear">
                  <li>
                    <el-tooltip class="item" effect="dark" content="暂无此功能" placement="bottom">
                      <i class="el-icon-menu"></i>
                    </el-tooltip>
                  </li>
                  <li>
                    <el-popover placement="top" popper-class="searchBox">
                      <el-input placeholder="请输入搜索内容..." v-model="newslist" clearable prefix-icon="el-icon-search"></el-input>
                      <el-tooltip slot="reference" class="item" effect="dark" content="搜索" placement="bottom">
                        <i class="el-icon-search"></i>
                      </el-tooltip>
                    </el-popover>
                  </li>
                </ul>
              </div>
              <div class="ListMenu">
                <div class="tooltip">
                  <i class="fas fa-crop-alt"></i> Find All Technology News
                </div>
                <div class="ListShow">
                  <el-scrollbar style="height: 100%">
                    <ul>
                      <li v-for="(item,index) in ContentList" :key="index" :class="{selectList:index==listChoice[0]}" @click="SelectList(index)">
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#c3c3c3;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle overhidden">
                              Monday sharing meeting
                            </div>
                            <div class="eachContent">
                              <p class="overhidden">Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
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
                <el-button icon="el-icon-plus" circle size="medium" @click="newsEditor=true"></el-button>
              </div>
            </el-col>
            <el-col :span="16" class="ContentArea">
              <div class="contentHeader">
                <el-dropdown trigger="click">
                  <span class="el-dropdown-link">
                    <i class="el-icon-more"></i>
                  </span>
                  <el-dropdown-menu slot="dropdown" class="dropdownPosition2">
                    <!-- <el-dropdown-item><i class="el-icon-setting"> </i>配置</el-dropdown-item> -->
                    <el-dropdown-item><i class="el-icon-close"> </i>退出</el-dropdown-item>
                  </el-dropdown-menu>
                </el-dropdown>
              </div>
              <div class="function">
                <i class="el-icon-edit" @click="newsEditor=true"></i>
                <i class="el-icon-delete"></i>
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
                        <p id="newsCopy">Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
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
        <div class="NewPart BoxSize">
          <el-row>
            <el-col :span="8" class="ListArea">
              <div class="AreaHeader">
                <ul class="clear">
                  <li>
                      <el-dropdown trigger="click"> <!-- @command="handleCommand" -->
                      <span class="el-dropdown-link">
                        <el-tooltip class="item" effect="dark" content="菜单栏" placement="right">
                          <i class="el-icon-menu"></i>
                        </el-tooltip>
                      </span>
                      <el-dropdown-menu slot="dropdown" class="dropdownPosition1">
                        <el-dropdown-item command="a">黄金糕</el-dropdown-item>
                        <el-dropdown-item command="b">狮子头</el-dropdown-item>
                        <el-dropdown-item command="c">螺蛳粉</el-dropdown-item>
                        <el-dropdown-item command="d" disabled>双皮奶</el-dropdown-item>
                        <el-dropdown-item command="e" divided>蚵仔煎</el-dropdown-item>
                      </el-dropdown-menu>
                    </el-dropdown>
                  </li>
                  <li>
                    <el-popover placement="top" popper-class="searchBox">
                      <el-input placeholder="请输入搜索内容..." v-model="postslist" clearable prefix-icon="el-icon-search"></el-input>
                      <el-tooltip slot="reference" class="item" effect="dark" content="搜索" placement="bottom">
                        <i class="el-icon-search"></i>
                      </el-tooltip>
                    </el-popover>
                  </li>
                </ul>
              </div>
              <div class="ListMenu">
                <div class="tooltip">
                  <i class="fas fa-crop-alt"></i> Find All Technology Posts
                </div>
                <div class="ListShow">
                  <el-scrollbar style="height: 100%">
                    <ul>
                      <li v-for="(item,index) in ContentList" :key="index" :class="{selectList:index==listChoice[1]}" @click="SelectList(index)">
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#c3c3c3;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle overhidden">
                              Monday sharing meeting
                            </div>
                            <div class="eachContent">
                              <p class="overhidden">Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
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
                <el-button icon="el-icon-plus" circle size="medium" @click="postsEditor=true"></el-button>
              </div>
            </el-col>
            <el-col :span="16" class="ContentArea">
              <div class="contentHeader">
                <el-dropdown trigger="click">
                  <span class="el-dropdown-link">
                    <i class="el-icon-more"></i>
                  </span>
                  <el-dropdown-menu slot="dropdown" class="dropdownPosition2">
                    <!-- <el-dropdown-item><i class="el-icon-setting"> </i>配置</el-dropdown-item> -->
                    <el-dropdown-item><i class="el-icon-close"> </i>退出</el-dropdown-item>
                  </el-dropdown-menu>
                </el-dropdown>
              </div>
              <div class="function">
                <i class="el-icon-edit" @click="postsEditor=true"></i>
                <i class="el-icon-delete"></i>
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
                        <h2>Tuesday sharing meeting</h2>
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
        <div class="NewPart BoxSize">
          <el-row>
            <el-col :span="8" class="ListArea">
              <div class="AreaHeader">
                <ul class="clear">
                  <li>
                      <el-dropdown trigger="click"> <!-- @command="handleCommand" -->
                      <span class="el-dropdown-link">
                        <el-tooltip class="item" effect="dark" content="菜单栏" placement="right">
                          <i class="el-icon-menu"></i>
                        </el-tooltip>
                      </span>
                      <el-dropdown-menu slot="dropdown" class="dropdownPosition1">
                        <el-dropdown-item command="a">黄金糕</el-dropdown-item>
                        <el-dropdown-item command="b">狮子头</el-dropdown-item>
                        <el-dropdown-item command="c">螺蛳粉</el-dropdown-item>
                        <el-dropdown-item command="d" disabled>双皮奶</el-dropdown-item>
                        <el-dropdown-item command="e" divided>蚵仔煎</el-dropdown-item>
                      </el-dropdown-menu>
                    </el-dropdown>
                  </li>
                  <li>
                    <el-popover placement="top" popper-class="searchBox">
                      <el-input placeholder="请输入搜索内容..." v-model="userslist" clearable prefix-icon="el-icon-search"></el-input>
                      <el-tooltip slot="reference" class="item" effect="dark" content="搜索" placement="bottom">
                        <i class="el-icon-search"></i>
                      </el-tooltip>
                    </el-popover>
                  </li>
                </ul>
              </div>
              <div class="ListMenu">
                <div class="tooltip">
                  <i class="fas fa-crop-alt"></i> Find All Interested Users
                </div>
                <div class="ListShow">
                  <el-scrollbar style="height: 100%">
                    <ul>
                      <li v-for="(item,index) in ContentList" :key="index" :class="{selectList:index==listChoice[2]}" @click="SelectList(index)">
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#c3c3c3;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle overhidden">
                              yao1508728331@gmail.com
                            </div>
                            <div class="eachContent">
                              <p class="overhidden">Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
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
                <el-button icon="el-icon-plus" circle size="medium" @click="usersEditor=true"></el-button>
              </div>
            </el-col>
            <el-col :span="16" class="ContentArea">
              <div class="contentHeader">
                <el-dropdown trigger="click">
                  <span class="el-dropdown-link">
                    <i class="el-icon-more"></i>
                  </span>
                  <el-dropdown-menu slot="dropdown" class="dropdownPosition2">
                    <!-- <el-dropdown-item><i class="el-icon-setting"> </i>配置</el-dropdown-item> -->
                    <el-dropdown-item><i class="el-icon-close"> </i>退出</el-dropdown-item>
                  </el-dropdown-menu>
                </el-dropdown>
              </div>
              <div class="function">
                <i class="el-icon-edit" @click="usersEditor=true"></i>
                <i class="el-icon-delete"></i>
              </div>
              <div class="contentShow">
                <el-scrollbar style="height:100%">
                  <div class="top">
                    <el-row :gutter=30>
                      <el-col :span="2" class="left-icon">
                        <i class="fas fa-quote-left"></i>
                      </el-col>
                      <el-col :span="22" class="right-content">
                        <p class="time">CREATED AT: 22TH JULY 2018</p>
                        <h2 class="userIntro"> Sagacious Jetty</h2>
                      </el-col>
                    </el-row>
                  </div>
                  <div class="bottom">
                    <el-row :gutter=30>
                      <el-col :span="2" class="left-icon"></el-col>
                      <el-col :span="22" class="right-content user-content">
                        <div>
                          <p>Email Address：<span>yao1508728331@gmail.com</span></p>
                        </div>
                        <div>
                            <p>User Introduce：</p>
                            <p>你好Lorem ipsum dolor sit amet consectetur adipisicing elit. Ea dolor a distinctio vero omnis saepe totam. Quod, accusantium! Cumque unde recusandae eius consequatur, mollitia id illum quos nisi quae deleniti!</p>
                        </div>
                        <div>
                            <el-collapse v-model="activeName" accordion>
                              <el-collapse-item title="评论历史 UserComments" name="1">
                                <el-table :data="UserDatas" style="width: 100%">
                                  <el-table-column type="expand">
                                    <template slot-scope="props">
                                      <el-form label-position="left" inline class="demo-table-expand">
                                        <el-form-item label="Comment IDnumber">
                                          <span>{{ props.row.commentId }}</span>
                                        </el-form-item>
                                        <el-form-item label="User Email">
                                          <span>{{ props.row.email }}</span>
                                        </el-form-item>
                                        <el-form-item label="Comment AllContent" class="commentWidth">
                                          <span>{{ props.row.commentData }}</span>
                                        </el-form-item>
                                      </el-form>
                                    </template>
                                  </el-table-column>
                                  <el-table-column  prop="created_at" width="170px"></el-table-column>
                                  <el-table-column  prop="postTitle"></el-table-column>
                                </el-table>
                              </el-collapse-item>
                            </el-collapse>
                        </div>
                      </el-col>
                    </el-row>
                  </div>
                </el-scrollbar>
              </div>
            </el-col>
          </el-row>
        </div>
        <div class="NewPart BoxSize">
          <el-row>
            <el-col :span="8" class="ListArea">
              <div class="AreaHeader">
                <ul class="clear">
                  <li>
                      <el-dropdown trigger="click"> <!-- @command="handleCommand" -->
                      <span class="el-dropdown-link">
                        <el-tooltip class="item" effect="dark" content="菜单栏" placement="right">
                          <i class="el-icon-menu"></i>
                        </el-tooltip>
                      </span>
                      <el-dropdown-menu slot="dropdown" class="dropdownPosition1">
                        <el-dropdown-item command="a">黄金糕</el-dropdown-item>
                        <el-dropdown-item command="b">狮子头</el-dropdown-item>
                        <el-dropdown-item command="c">螺蛳粉</el-dropdown-item>
                        <el-dropdown-item command="d" disabled>双皮奶</el-dropdown-item>
                        <el-dropdown-item command="e" divided>蚵仔煎</el-dropdown-item>
                      </el-dropdown-menu>
                    </el-dropdown>
                  </li>
                  <li>
                    <el-popover placement="top" popper-class="searchBox">
                      <el-input placeholder="请输入搜索内容..." v-model="commentslist" clearable prefix-icon="el-icon-search"></el-input>
                      <el-tooltip slot="reference" class="item" effect="dark" content="搜索" placement="bottom">
                        <i class="el-icon-search"></i>
                      </el-tooltip>
                    </el-popover>
                  </li>
                </ul>
              </div>
              <div class="ListMenu">
                <div class="tooltip">
                  <i class="fas fa-crop-alt"></i> Find All Kinds of Comments
                </div>
                <div class="ListShow">
                  <el-scrollbar style="height: 100%">
                    <ul>
                      <li v-for="(item,index) in ContentList" :key="index" :class="{selectList:index==listChoice[3]}" @click="SelectList(index)">
                        <el-row>
                          <el-col :span="3">
                            <div class="tip">
                              N
                            </div>
                            <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#c3c3c3;cursor:pointer;line-height: 20px;"></i>
                          </el-col>
                          <el-col :span="21">
                            <div class="authorName">
                              Sagacious Jetty
                              <i class="fas fa-star"></i>
                            </div>
                            <div class="eachTitle overhidden">
                              Monday sharing meeting
                            </div>
                            <div class="eachContent">
                              <p class="overhidden">Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
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
                <el-button icon="el-icon-plus" circle size="medium" @click="ErrorMess()"></el-button>
              </div>
            </el-col>
            <el-col :span="16" class="ContentArea">
              <div class="contentHeader">
                <el-dropdown trigger="click">
                  <span class="el-dropdown-link">
                    <i class="el-icon-more"></i>
                  </span>
                  <el-dropdown-menu slot="dropdown" class="dropdownPosition2">
                    <!-- <el-dropdown-item><i class="el-icon-setting"> 配置</i></el-dropdown-item> -->
                    <el-dropdown-item><i class="el-icon-close"> 退出</i></el-dropdown-item>
                  </el-dropdown-menu>
                </el-dropdown>
              </div>
              <div class="function">
                <i class="el-icon-edit" @click="ErrorMess()"></i>
                <i class="el-icon-delete"></i>
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
                        <h2>For: Tuesday sharing meeting</h2>
                        <el-tag size="small" type="info" closable>Sagacious Jetty (Email: yao1508728331@gmail.com)</el-tag>
                      </el-col>
                    </el-row>
                  </div>
                  <div class="bottom">
                    <el-row :gutter=30>
                      <el-col :span="2" class="left-icon"></el-col>
                      <el-col :span="22" class="right-content">
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, quo perferendis. Distinctio, rem sint nostrum corrupti architecto similique illo aperiam doloremque ex recusandae voluptatibus quo error unde hic minus ipsa.</p>
                        <div class="replyContent">
                          <h2>Comment Replies</h2>
                          <div class="replyArea">
                            <ul>
                              <li>
                                <el-row>
                                  <el-col :span="3">
                                    <div class="tip">
                                      N
                                    </div>
                                    <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#c3c3c3;cursor:pointer;line-height: 20px;"></i>
                                  </el-col>
                                  <el-col :span="21">
                                    <div class="authorName">
                                      Sagacious Jetty (Email: yao1508728331@gmail.com)
                                      <i class="fas fa-star"></i>
                                    </div>
                                    <div class="eachTitle overhidden">
                                      What does it contain...
                                    </div>
                                    <div class="eachContent">
                                      <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
                                      <span class="eachDay">Created at: 100 days ago</span>
                                    </div>
                                  </el-col>
                                </el-row>
                                <div class="actionDone">
                                  <span>
                                    <el-tooltip content="Reply It" placement="top">
                                      <i class="el-icon-message"></i>
                                    </el-tooltip>
                                  </span>
                                  <span>
                                    <el-tooltip content="Delete this Reply" placement="top">
                                      <i class="el-icon-delete"></i>
                                    </el-tooltip>
                                  </span>
                                </div>
                              </li>
                              <li>
                                <el-row>
                                  <el-col :span="3">
                                    <div class="tip">
                                      N
                                    </div>
                                    <i class="el-icon-more" style="padding: 2px 0 0 4px;color:#c3c3c3;cursor:pointer;line-height: 20px;"></i>
                                  </el-col>
                                  <el-col :span="21">
                                    <div class="authorName">
                                      Sagacious Jetty (Email: yao1508728331@gmail.com)
                                      <i class="fas fa-star"></i>
                                    </div>
                                    <div class="eachTitle overhidden">
                                      What does it contain...
                                    </div>
                                    <div class="eachContent">
                                      <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit...</p>
                                      <span class="eachDay">Created at: 100 days ago</span>
                                    </div>
                                  </el-col>
                                </el-row>
                                <div class="actionDone">
                                  <span>
                                    <el-tooltip content="Reply It" placement="top">
                                      <i class="el-icon-message"></i>
                                    </el-tooltip>
                                  </span>
                                  <span>
                                    <el-tooltip content="Delete this Reply" placement="top">
                                      <i class="el-icon-delete"></i>
                                    </el-tooltip>
                                  </span>
                                </div>
                              </li>
                            </ul>
                          </div>
                        </div>
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
    <div class="dialogArea">
      <message-box :messageBox.sync="messageBox"></message-box>
      <personal-infor :personalInfor.sync="personalInfor"></personal-infor>
      <news-editor :newsEditor.sync="newsEditor"></news-editor>
      <posts-editor :postsEditor.sync="postsEditor"></posts-editor>
      <users-editor :usersEditor.sync="usersEditor"></users-editor>
    </div>
  </div>
</template>

<script>
import MessageBox from './messageBox.vue'
import PersonalInfor from './personalInfor.vue'
import NewsEditor from './NewsEditor.vue'
import PostsEditor from './PostsEditor.vue'
import UsersEditor from './UsersEditor.vue'
export default {
  components: {MessageBox, PersonalInfor, NewsEditor, PostsEditor, UsersEditor},
  name: 'Index',
  props: {
    msg: String
  },
  data() {
    return {
      activeName: '1',
      LinkChange: 0,
      clist: 0,
      listChoice: [0, 0, 0, 0],
      ContentList: ['1','2','3','4'],
      Top: 'margin-top: 0',
      newslist: '',
      postslist: '',
      userslist: '',
      commentslist: '',
      UserDatas: [{
          created_at: '22TH JULY 2018',
          username: '好滋好味鸡蛋仔',
          postTitle: '荷兰优质淡奶，奶香浓而不腻',
          commentData: '上海市普陀区真北路',
          commentId: '2',
          email: 'yao1508728331@gmail.com'
        }, {
          created_at: '22TH JULY 2018',
          username: '好滋好味鸡蛋仔',
          postTitle: '荷兰优质淡奶，奶香浓而不腻',
          commentData: '上海市普陀区真北路',
          commentId: '2',
          email: 'yao1508728331@gmail.com'
        }, {
          created_at: '22TH JULY 2018',
          username: '好滋好味鸡蛋仔',
          postTitle: '荷兰优质淡奶，奶香浓而不腻',
          commentData: '上海市普陀区真北路',
          commentId: '2',
          email: 'yao1508728331@gmail.com'
        }, {
          created_at: '22TH JULY 2018',
          username: '好滋好味鸡蛋仔',
          postTitle: '荷兰优质淡奶，奶香浓而不腻',
          commentData: '上海市普陀区真北路',
          commentId: '2',
          email: 'yao1508728331@gmail.com'
        }],
      messageBox: false,
      personalInfor: false,
      newsEditor: false,
      postsEditor: false,
      usersEditor: false
    }
  },
  methods: {
    changeSelectStatus: function (index) {
      this.LinkChange = index
      // this.clist = this.listChoice[index]
      let bodyHeight = document.documentElement.clientHeight >= 662 ? 662 : document.documentElement.clientHeight
      this.Top = 'margin-top: ' + (-index * bodyHeight) + 'px'
    },
    SelectList: function (index) {
      // this.listChoice[this.LinkChange] = index
      this.$set(this.listChoice, this.LinkChange, index);
      // this.clist = this.listChoice[this.LinkChange]
    },
    ErrorMess: function () {
      this.$message({
        showClose: true,
        message: '评论模块未设置管理员创建/修改功能',
        type: 'warning'
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.dashboard{
  position: fixed;
  left: 0;
  top: 0;
  box-shadow: 2px 0 10px #c3c3c3;
  z-index: 2000;
  header{
    padding: 10px 35px;
    border-bottom: 2px solid #f1f2f6;
    .logo{
      font-size: 30px;
      color: #668efd;
      line-height: 36px;
      i{
        font-size: 21px;
        vertical-align: middle;
        padding: 0 4px 0 2px;
      }
      .logoName{
        font-size: 18px;
        font-weight: bolder;
        padding-left: 3px;
        text-transform: uppercase;
      }
    }
    .messageTip{
      text-align: right;
      line-height: 40px;
      color: #c3c3c3;
      i{
        cursor: pointer;
      }
    }
  }
  .routeLink{
    padding: 50px 35px;
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
        font-size: 13px;
        color: #868688;
        font-weight: bold;
        li{
          position: relative;
          cursor: pointer;
          padding: 15px 5px;
          i{
            padding-right: 13px;
            color: #c3c3c3;
            width: 26px;
          }
          &:hover,&:hover i{
            color: #668efd81;
          }
          .count{
            position: absolute;
            right: 5px;
            display: inline;
            border-radius: 7px;
            border: 1px solid #c3c3c3;
            padding: 0 6px;
            font-size: 11px;
            font-weight: normal;
          }
          .newTip{
            background-color: #668efd;
            color: #fff;
            border: 0;
            padding: 1px 5px;
          }
          &:hover .count{
            border-color: #668efd;
          }
          &:hover .newTip{
            border-color: transparent;
          }
        }
        li.selectLink{
          color: #668efd;
        }
      }
    }
    .aphorism{
      margin-top: 13px;
      div{
        color: #868688;
        font-size: 13px;
        padding: 13px 5px;
        font-weight: bold;
        i{
          padding-right: 13px;
        }
      }
    }
  }
  .postNum{
    height: calc(100% - 540px);
    position: relative;
    cursor: default;
    .progress{
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%);
      width: 76%;
        // width: 75%;
        // margin: 0 auto;
        // margin-top: 15%;
      p{
        font-size: 12px;
        color: #c3c3c3;
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
  z-index: 1;
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
            color: #c3c3c3;
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
          // font-weight: bold;
          font-size: 12px;
          color: #c3c3c3;
          padding: 15px 30px;
          i{
            padding-left: 5px;
            padding-right: 11px;
          }
        }
        .ListShow{
          height: 431px;
          ul{
            li{
              padding: 28px 30px;
              // font-weight: bold;
              border-top: 2px solid #f1f2f6;
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
                color: #c3c3c3;
                line-height: 24px;
              }
              .authorName{
                position: relative;
                i{
                  position: absolute;
                  right: 0;
                  top: 0;
                  // transform: translateY(-50%);
                  line-height: 24px;
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
                // font-weight: bold;
                // overflow: hidden;
                // text-overflow:ellipsis;
                // white-space: nowrap;
              }
              .eachContent{
                position: relative;
                line-height: 20px;
                p{
                  width: 59%;
                  // overflow: hidden;
                  // text-overflow:ellipsis;
                  // white-space: nowrap;
                }
                span{
                  position: absolute;
                  right: 0;
                  top: 0;
                }
              }
            }
            li.selectList{
              background-color: #fff;
            }
          }
        }
      }
      .addContent{
        height: calc(100% - 530px);
        position: relative;
        .el-button{
          // display: block;
          // margin: 32px auto;
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%,-50%);
          background-color: #668efd;
          color: #fff;
          &:hover{
            background-color: #7da0ff;
          }
        }
      }
    }
    .ContentArea{
      width: 69%;
      .contentHeader{
        padding: 9.5px 35px;
        line-height: 41px;
        text-align: right;
        border-bottom: 2px solid #f1f2f6;
        .el-dropdown{
          color: #c3c3c3;
          line-height: 1;
          i{
            cursor: pointer;
            color: #c3c3c3;
            font-size: 14px;
            &:hover{
              color: #7da0ff;
            }
          }
        }
      }
      .function{
        padding: 25px 35px 5px;
        color: #c3c3c3;
        text-align: right;
        i{
          padding: 0 0 0 20px;
          cursor: pointer;
          font-size: 16px;
          &:hover{
            color: #7da0ff;
          }
        }
      }
      .contentShow{
        height: calc(100% - 153px);
        .top{
          padding: 10px 35px 15px;
          .left-icon{
            text-align: right;
            padding-top: 26px;
            i{
              font-size: 20px;
              color: #7da0ff;
            }
          }
          .right-content{
            letter-spacing: 1px;
            p.time{
              font-size: 12px;
              color: #c3c3c3;
              letter-spacing: 1.5px;
            }
            h2{
              padding: 6px 25px 6px 0;
              font-size: 32px;
              color: #868688;
            }
            h2.userIntro{
              padding: 70px 0 10px 15px;
              margin-top: 10px;
              color: #fff;
              background-color: #7da0ff;
              text-transform: uppercase;
              border-bottom-left-radius: 20px;
              border-top-right-radius: 30px;
              &::before{
                content: '';
                display: inline-block;
                width: 15px;
                height: 25px;
                background-color: #fff;
              }
            }
            .el-tag{
              background-color: #fff;
              border-color: #c3c3c3;
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
              padding-left: 6px;
              font-size: 15px;
              color: #868688;
            }
            .replyContent{
              padding: 0 25px 0 6px;
              h2{
                color: #868688;
                padding: 25px 0 10px;
                font-size: 20px;
              }
              .replyArea{
                li{
                  padding: 20px 30px 7px 5px;
                  font-weight: bold;
                  border-bottom: 2px solid #f1f2f6;
                  cursor: default;
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
                    color: #8e8f92;
                    line-height: 24px;
                  }
                  .authorName{
                    position: relative;
                    i{
                      color: #c3c3c3;
                      position: absolute;
                      right: 0;
                      top: 0;
                      line-height: 24px;
                      // transform: translateY(-50%);
                      cursor: pointer;
                      &:hover{
                        color: #ffc8c7;
                      }
                    }
                  }
                  .eachTitle{
                    color: #c3c3c3;
                    line-height: 22px;
                    font-size: 15px;
                    // overflow: hidden;
                    // text-overflow:ellipsis;
                    // white-space: nowrap;
                  }
                  .eachContent{
                    position: relative;
                    line-height: 20px;
                    p{
                      color: #8e8f92;
                      padding-left: 0;
                      font-size: 12px;
                    }
                    span{
                      font-weight: 500;
                      position: absolute;
                      right: 0;
                      top: calc(100% + 13px);
                    }
                  }
                  .actionDone{
                    color: #8e8f92;
                    font-size: 13px;
                    padding: 15px 0;
                    i{
                      padding-right: 15px;
                      cursor: pointer;
                    }
                  }
                }
              }
            }
          }
          .user-content{
            font-size: 14px;
            color: #868688;
            >div{
              padding: 5px 5px 5px 15px;
              p{
                font-size: 13px;
                padding: 3px 0;
                line-height: 17px;
              }
            }
          }
        }
      }
    }
  }
  .PositionChange{
    transition: margin-top .6s;
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
.dropdownPosition2{
  top: 30px !important;
  left: 1246px !important;
  li{
    font-size: 13px !important;
    padding: 0 32px !important;
    i{
      padding-right: 10px;
    }
  }
  .popper__arrow{
    left: 71px !important;
  }
  
}
.dropdownPosition1{
    top: 34px !important;
    left: 514px !important;
}
.el-tag .el-icon-close{
  top: 0 !important;
}
.el-collapse-item__header,.el-collapse-item__content{
  color: #868688 !important;
}
.user-content{
  .el-table__header-wrapper{
    display: none;
  }
  .el-collapse-item__content{
    .el-table{
      color: #868688;
      font-size: 12px;
      td,th{
        padding: 9px 0;
      }
      .demo-table-expand label {
        color: #99a9bf;
      }
      .demo-table-expand .commentWidth{
        label{
          width: 100%;
        }
      }
      .el-form--inline{
        background-color: #f8f8f8;
      }
      .demo-table-expand .el-form-item {
        margin-right: 0;
        margin-bottom: 0;
        min-width: 30%;
        padding-left: 60px;
      }
      .el-form-item__content,.el-form-item__label{
        font-size: 12px;
        line-height: 30px;
      }
    }
  }
}
.searchBox{
  padding: 7px 10px !important;
  top: 50px !important;
  left: 286px !important;
  background-color: rgb(245, 246, 250) !important;
  box-shadow: none !important;
  border-radius: 0 !important;
  border: 0 !important;
  z-index: 1000 !important;
  i{
    padding-left: 18px;
    line-height: 31px !important;
  }
  .el-icon-circle-close{
    padding-left: 0;
  }
  input{
    color: #c3c3c3;
    width: 313px;
    line-height: 26px;
    height: 32px;
    font-size: 13px;
    border: 1px solid #f1f2f6;
    padding-left: 51px !important;
    // text-align: center;
  }
  .el-input__inner:hover,.el-input__inner:focus{
    border-color: #f1f2f6;
  }
  .popper__arrow{
    display: none !important;
  }
}
</style>

