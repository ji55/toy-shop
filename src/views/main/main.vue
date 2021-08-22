<template>
  <MainHeader/>
  <div class="container">
    <div class="main-img-wrap">
      <img class="main-img" 
        src="@/assets/images/toy-main.jpg" 
        @mouseenter="mainImgHover"
        @mouseleave="mainImgHover">
      <div v-if="info.mainImgHover">
        <span class="main-img-title">초록 개구리 커밋</span>
        <p class="main-img-text"> 
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatum delectus voluptatibus cupiditate aut, eligendi aspernatur molestias fuga sint odio architecto reprehenderit numquam natus commodi alias doloribus soluta sapiente dolor? Sequi!</p>
      </div>
      <button class="main-img-btn">알아보기 →</button>
    </div>

    <el-row class="sub-img sub-img-wrap">
      <img class="sub-img1"
           src="@/assets/images/happy.jpg" 
           style="margin-right:2%"
           @mouseenter="subImg1Hover"
           @mouseleave="subImg1Hover">
      <div v-if="info.subImg1Hover">
        <span class="sub-img-title">행복한 양 인형</span>
        <p class="sub-img-text"> 
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatum delectus voluptatibus cupiditate aut, eligendi aspernatur molestias fuga sint odio architecto reprehenderit numquam natus commodi alias doloribus soluta sapiente dolor? Sequi!</p>
      </div>
      <img class="sub-img2"
           src="@/assets/images/teddybear.jpg" 
           @mouseenter="subImg2Hover"
           @mouseleave="subImg2Hover">
      <div v-if="info.subImg2Hover">
        <span class="sub-img2-title">테디베어</span>
        <p class="sub-img2-text"> 
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatum delectus voluptatibus cupiditate aut, eligendi aspernatur molestias fuga sint odio architecto reprehenderit numquam natus commodi alias doloribus soluta sapiente dolor? Sequi!</p>
      </div>
    </el-row>

    <div style="margin-top: 70px;">
      <div style="float: left;"><h4>새로 등록된 장난감</h4></div>
      <div style="float: right;">
        <!-- 왼쪽 버튼 -->
        <i class="el-icon-arrow-left" v-if="info.toyPage == 0" style="color:lightgray"></i>
        <i class="el-icon-arrow-left" v-else @click="pagePre"></i>
        <!-- 오른쪽 버튼 -->
        <i class="el-icon-arrow-right" v-if="info.toyPage == 1" style="color:lightgray"></i>
        <i class="el-icon-arrow-right" v-else @click="pageNext"></i>
      </div>
    </div>
    <br><br>
    <div class="newToy" v-for="(toy, idx) in info.newToy[info.toyPage]" :key="idx">
      <card :toy="toy"/>
    </div>
  </div>
    <MainFooter/>
</template>

<script>
import { reactive } from '@vue/reactivity';
import MainHeader from './components/main-header'
import MainFooter from './components/main-footer'
import Card from './components/card'

export default {
  name: "Main",
  components: {
    MainHeader,
    MainFooter,
    Card
  },
  props: {
    msg: String,
  },
  setup() {
    const info = reactive({
      mainImgHover: false,
      subImg1Hover: false,
      subImg2Hover: false,
      toyPage: 0,
      newToy: [[
        {"title": "피규어", "pId": "1"},
        {"title": "구슬", "pId": "2"},
        {"title": "미니언즈", "pId": "3"},
        {"title": "미니언즈 파리", "pId": "4"},
        {"title": "오리들", "pId": "5"},
      ], [
        {"title": "물놀이", "pId": "6"},
        {"title": "사자 인형", "pId": "7"},
        {"title": "마리오", "pId": "8"},
        {"title": "곰돌이 인형", "pId": "9"},
        {"title": "분홍 주사위", "pId": "10"},
      ]
      ]
    })

    const mainImgHover = function () {
      if (info.mainImgHover) {
        info.mainImgHover = false
      } else {
        info.mainImgHover = true
      }
    }

    const subImg1Hover = function () {
      if (info.subImg1Hover) {
        info.subImg1Hover = false
      } else {
        info.subImg1Hover = true
      }
    }

    const subImg2Hover = function () {
      if (info.subImg2Hover) {
        info.subImg2Hover = false
      } else {
        info.subImg2Hover = true
      } 
    }

    const pagePre = function () {
      info.toyPage = 0
    }

    const pageNext = function () {
      info.toyPage = 1
    }

    return { info, mainImgHover, subImg1Hover, subImg2Hover, pagePre, pageNext }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main-img-wrap {
  width: 100%;
  margin: 10px auto;
  position: relative;
}
.sub-img-wrap {
  width: 100%;
  /* margin: 10px auto; */
  position: relative;
}

.main-img {
  width: 100%;
  height: 450px;
}

.main-img:hover {
  opacity: 0.5;
  transition-property: opacity;
  transition-duration: 1s;
}

.sub-img1:hover, .sub-img2:hover {
  opacity: 0.5;
  transition-property: opacity;
  transition-duration: 1s;
}

.main-img-title {
  color: black;
  position: absolute;
  font-size: 30px;
  font-weight: 800;
  font-family: Arial, Helvetica, sans-serif;
  top: 10%;
  left: 5%;
  z-index: -1;
}

.main-img-text {
  color: black;
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  top: 30%;
  left: 5%;
  right: 5%;
  z-index: -1;
}

.main-img-btn {
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  position: absolute;
  padding: 15px 32px;
  font-size: 20px;
  top: 80%;
  left: 5%;
}

.sub-img > img {
  width: 49%;
  height: 400px;
  margin-top: 10px;
}

.sub-img-title {
  color: black;
  position: absolute;
  font-size: 30px;
  font-weight: 800;
  font-family: Arial, Helvetica, sans-serif;
  top: 10%;
  left: 3%;
  z-index: -1;
}

.sub-img-text {
  color: black;
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  top: 30%;
  left: 3%;
  right: 53%;
  z-index: -1;
}

.sub-img2-title {
  color: black;
  position: absolute;
  font-size: 30px;
  font-weight: 800;
  font-family: Arial, Helvetica, sans-serif;
  top: 10%;
  left: 54%;
  z-index: -1;
}

.sub-img2-text {
  color: black;
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  top: 30%;
  left: 54%;
  right: 3%;
  z-index: -1;
}

h4 {
  margin-bottom: 10px; 
  font-weight: 900;
  font-family: Arial, Helvetica, sans-serif;
}

.newToy {
  display:inline;
  margin-right: 15px;
  text-align: center;
}
</style>
