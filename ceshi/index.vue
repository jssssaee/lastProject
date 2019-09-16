<template>
  <div id="index">
    <div class="header-bar">
      <el-row class="row_top">
        <el-col :span="8">
          <ul class="col_top first-level col_lift" v-bind:class="{active2:$store.state.build}">
            <li class>
              <span>Hi，欢迎来到百度糯米</span>
            </li>
            <li class="login">
              <a href="#" @click="login">请登录</a>
            </li>
            <li class="reg">
              <a href="#" @click="regist">免费注册</a>
            </li>
          </ul>
          <template v-if="$store.state.build">
            <div class="build">
              <div style="float:left" class="username">用户：{{$store.state.name}} 欢迎登陆!</div>
              <div v-on:click="out" class="out">退出</div>
            </div>
          </template>
        </el-col>
        <el-col :span="5">
          <div class="col_top"></div>
        </el-col>
        <el-col :span="11">
          <ul class="col_top first-level col_right">
            <li>
              <a href="#">个人中心</a>
            </li>
            <li>
              <el-popover placement="top" width="240" trigger="hover" class="col_after">
                <div class="el_popover_div1">暂无浏览记录</div>
                <el-link href="#" slot="reference">
                  最近浏览
                  <span class="arrow-down-logo"></span>
                </el-link>
              </el-popover>
              <span class="sep_lines"></span>
            </li>
            <li>
              <el-popover placement="top" width="150" trigger="hover" class="col_after">
                <div class="el_popover_div2">
                  <img
                    src="//gss0.bdstatic.com/8r1VfDn9KggZnd_b8IqT0jB-xx1xbK/static/common/img/new/qr-code-re-text_2b92f31.png"
                    alt
                  />
                </div>
                <el-link href="#" slot="reference">
                  糯米APP
                  <span class="arrow-down-logo"></span>
                </el-link>
              </el-popover>
            </li>
            <li>
              <!-- <a href="#">我是商家</a> -->
              <el-popover placement="top" width="150" trigger="hover" class="col_after">
                <div class="el_popover_div3">
                  <el-link href="#" slot="reference">商户中心</el-link>
                  <el-link href="#" slot="reference">我想合作</el-link>
                </div>
                <el-link href="#" slot="reference">
                  糯米APP
                  <span class="arrow-down-logo"></span>
                </el-link>
              </el-popover>
              <span class="sep_lines"></span>
            </li>
            <li>
              <a href="#">帮助中心</a>
            </li>
            <li>
              <a href="#">食品安全</a>
            </li>
          </ul>
        </el-col>
      </el-row>
    </div>

    <div class="header_input">
      <div class="logo-area">
        <a href="#">
          <img
            src="//gss0.bdstatic.com/8r1VfDn-KggZnd_b8IqT0jB-xx1xbK/static/common/nis_index/sub/img/re-logo_7c90a10.png"
            alt
          />
        </a>
        <div class="city-wrap">
          <span class="city-pos"></span>
          <span>成都</span>
          <span class="arrow-down-line"></span>
        </div>
      </div>
      <div class="search-area">
        <div>
          <form action>
            <input type="text" class="searchinput" placeholder="搜索商家/地点" />
            <div class="searchbtn-wrap">
              <input type="submit" class="searchbtn" value />
              <span class="search-text">搜&nbsp;索</span>
            </div>
          </form>
        </div>
        <ul class="reco-list">
          <li>
            <a href="#">钢琴</a>
          </li>
          <li>
            <a href="#">大保健</a>
          </li>
          <li>
            <a href="#">化妆</a>
          </li>
          <li>
            <a href="#">小龙坎火锅</a>
          </li>
          <li>
            <a href="#">拔罐刮痧</a>
          </li>
        </ul>
      </div>
      <div class="utils">
        <div class="util-item">
          <div class="u-icon refund"></div>
        </div>
        <div class="util-item mid">
          <div class="u-icon pei"></div>
        </div>
        <div class="util-item">
          <div class="u-icon money"></div>
        </div>
      </div>
      <div class="shopCar">
        <div class="cw-icon">
          <i class="el-icon-shopping-cart-2"></i>
          <span>我的购物车</span>
          <el-badge :value="$store.state.count" class="item"></el-badge>
        </div>
        <div class="dropdown-layer">
          <ul>
            <li v-for="item in this.$store.state.shopCar" :key="item.index">
              <span class="movieName">{{item.title}}:</span>
              <span class="moviePrice">￥{{item.price}}</span>
            </li>
          </ul>
          <el-button type="danger" plain @click="buy">购买</el-button>
        </div>
      </div>
    </div>

    <div class="nav-inner">
      <el-container>
        <el-header height="44px">
          <div class="cate-row">
            <span class="item">全部分类</span>
            <span class="item_img"></span>
          </div>
          <div class="new-item">首页</div>
          <div class="new-item">酒店</div>
          <div class="new-item">出行</div>
          <div class="new-item">首页</div>
        </el-header>
        <el-container>
          <el-aside width="233px">
            <div class="level-item">
              <div
                :class="[index==flag?'active':'',first_level]"
                v-for="(item,index) in list.allClass"
                :key="index"
                @mouseover="aside_mouseenter(index)"
                @mouseout="aside_mouseleave()"
              >
                <dl>
                  <dt class="title">
                    <a href="#">{{item.name}}</a>
                  </dt>
                  <dd>
                    <a href="#">{{item.leader[0].item[0].itemName}}</a>
                    <!-- <a href="#">{{randomItemName}}</a> -->
                  </dd>
                  <dd>
                    /&nbsp;
                    <a href="#">{{item.leader[0].item[1].itemName}}</a>
                  </dd>
                </dl>
              </div>
            </div>
          </el-aside>
          <el-main>
            <div :class="[aside_right,{active:flag2}]">
              <!-- <div class="aside_right"> -->
              <div
                :class="[aside_right_outer,movie,special]"
                v-for="item in list.allClass[1].leader"
                :key="item.leaderName"
              >
                <div>{{item.leaderName}}</div>
                <div class>
                  <div v-for="item2 in item.item" :key="item2.itemName">{{item2.itemName}}</div>
                </div>
              </div>

              <div
                :class="[aside_right_outer,food]"
                v-for="item in list.allClass[2].leader"
                :key="item.leaderName"
              >
                <div>{{item.leaderName}}</div>
                <div class>
                  <div v-for="item2 in item.item" :key="item2.itemName">{{item2.itemName}}</div>
                </div>
              </div>

              <div
                :class="[aside_right_outer,play]"
                v-for="item in list.allClass[3].leader"
                :key="item.leaderName"
              >
                <div>{{item.leaderName}}</div>
                <div class>
                  <div v-for="item2 in item.item" :key="item2.itemName">{{item2.itemName}}</div>
                </div>
              </div>

              <div
                :class="[aside_right_outer,live]"
                v-for="item in list.allClass[4].leader"
                :key="item.leaderName"
              >
                <div>{{item.leaderName}}</div>
                <div class>
                  <div v-for="item2 in item.item" :key="item2.itemName">{{item2.itemName}}</div>
                </div>
              </div>

              <div
                :class="[aside_right_outer,beaut]"
                v-for="item in list.allClass[5].leader"
                :key="item.leaderName"
              >
                <div>{{item.leaderName}}</div>
                <div class>
                  <div v-for="item2 in item.item" :key="item2.itemName">{{item2.itemName}}</div>
                </div>
              </div>
            </div>
            <div class="main_box">
              <div></div>
              <div></div>
              <div></div>
            </div>
          </el-main>
        </el-container>
      </el-container>
    </div>
    <element0></element0>
    <router-view></router-view>
  </div>
</template>

<script>
import element0 from "./elementui";

export default {
  components: {
    element0
  },
  data() {
    return {
      aside_right_outer: "aside_right_outer",
      movie: "movie",
      food: "food",
      play: "play",
      live: "live",
      beaut: "beaut",
      special: "special",
      aside_right: "aside_right",
      first_level: "first-level",
      flag: 1000,
      flag2: true,
      visible: true,
      list: [],
      buyFlag: true
    };
  },

  mounted() {
    this.$nextTick(function() {
      this.$axios
        .get("http://192.168.2.121:8888/data", {
          params: {}
        })
        .then(
          function(response) {
            window.console.log(response.data);
            this.list = response.data;
          }.bind(this)
        )
        .catch(function(error) {
          window.console.log(error);
        });
    });
  },

  methods: {
    out: function() {
      this.$store.state.build = false;
    },
    login() {
      this.$router.push("/login");
    },
    regist() {
      this.$router.push("/regist");
    },
    buy: function() {
      if (this.buyFlag) {
        alert("请先登录");
        this.$router.push("/login");
        this.buyFlag = !this.buyFlag;
      } else {
        this.$axios
          .post("http://192.168.2.121:8888/buyShop", {
            list: this.$store.state.shopCar
          })
          .then(
            function(response) {
              window.console.log(response.data);
              this.list = response.data;
            }.bind(this)
          )
          .catch(function(error) {
            window.console.log(error);
          });
        alert("购买成功");
      }
    },
    aside_mouseenter: function(e) {
      if (e > 0 && e < 6) {
        this.flag2 = false;
        if (e == 1) {
          this.movie = "";
        } else if (e == 2) {
          this.food = "";
        } else if (e == 3) {
          this.play = "";
        } else if (e == 4) {
          this.live = "";
        } else if (e == 5) {
          this.beaut = "";
        }
      }

      return (this.flag = e);
    },
    aside_mouseleave: function() {
      this.flag2 = true;
      this.movie = "movie";
      this.food = "food";
      this.play = "play";
      this.live = "live";
      this.beaut = "beaut";
      return (this.flag = 1000);
    }
  },
  computed: {}
};
</script>


<style scoped>
@import url("../assets/css/index.css");
.active2 {
  display: none;
}
.username {
  margin-right: 30px;
}
.build {
  font-size: 14px;
  height: 40px;
  line-height: 40px;
}
.out {
  float: left;
  color: #d0a85d;
}
</style>