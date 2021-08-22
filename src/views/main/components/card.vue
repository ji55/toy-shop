<template>
  <el-row style="display:inline-block; margin-left:1%" >
    <el-col><img class="toy-img" 
                :src="info.imgUrl" 
                @mouseenter="ImgHover"
                @mouseleave="ImgHover">

    <div v-if="info.hover">
      <span class="img-title">{{ toy.title }}</span>
      <p class="img-text"> 
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatum delectus voluptatibus cupiditate aut</p>
    </div>

   <div class="toy-title">{{ toy.title }}</div>
    </el-col>
  </el-row>


</template>

<script>
import { onUpdated, reactive } from '@vue/runtime-core'
export default {
  props: ["toy"],

  setup(props){
    const info = reactive({
      imgUrl: '',
      hover: false,
    })

    info.imgUrl = require(`@/assets/images/${props.toy.pId}.jpg`)

    onUpdated(()=>{
      info.imgUrl = require(`@/assets/images/${props.toy.pId}.jpg`)
    })

    const ImgHover = function () {
      if (info.hover) {
        info.hover = false
      } else {
        info.hover = true
      }
    }

    return { info, ImgHover }
  }
}
</script>

<style scoped>
.toy-title {
  width: 230px; 
  text-align: left;
  margin-top: 5px;
  font-family: Arial, Helvetica, sans-serif;
}

.toy-img {
  width: 230px; 
  height: 200px;
}

.toy-img:hover {
  opacity: 0.5;
  transition-property: opacity;
  transition-duration: 1s;
}

.img-title {
  color: black;
  position: absolute;
  font-size: 20px;
  font-weight: 800;
  font-family: Arial, Helvetica, sans-serif;
  top: 5%;
  left: 5%;
  z-index: -1;
}

.img-text {
  color: black;
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  top: 30%;
  left: 2%;
  right: 2%;
  z-index: -1;
}

</style>