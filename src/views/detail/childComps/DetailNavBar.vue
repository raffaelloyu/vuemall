<template>
  <div>
    <nav-bar>
      <div slot="left" class="back" @click="back">
        <img src="~assets/img/detail/arrow-left.svg" alt="">
      </div>
      <div slot="center" class="title">
        <div v-for="(item, index) in titles"
             class="title-item"
             :class="{active: index === currentIndex}"
             @click="titleClick(index)">
          {{item}}</div>
      </div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
export default {
  name: "DetailNavBar",
  components: {NavBar},
  data() {
    return {
      titles: ['商品', '参数', '评论', '推荐'],
      currentIndex: 0
    }
  },
  methods:{
    titleClick(index){
      // console.log(index);
      this.currentIndex = index
      this.$emit('titleClick', index)
    },
    back(){
      this.$router.back()
    }
  }
}
</script>

<style scoped>
  .title{
    display: flex;
  }

  .title-item{
    flex: 1;
  }

  .active{
    color:var(--color-high-text)
  }

  .back{
    margin-top: 7px;


  }
</style>
