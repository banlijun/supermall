<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners='banners'/>
  </div>
</template>

 
<script>
  import NavBar from 'components/common/navbar/NavBar'
  import {HomeSwiper} from 'views/home/childComps/HomeSwiper' 

  import {getHomeMultidata} from 'network/home'
  export default {
    name: 'Home', 
    components: {
      NavBar,
      HomeSwiper
    },
    data() {
      return {
        banners: [],
        recommends: [],
      }
    },
    created() {
      this.getHomeMultidata()
    },
    methods: {
      getHomeMultidata(){
        getHomeMultidata().then(res => {
          this.banners = res.data.banner.list;
          this.recommends = res.data.recommend;
          console.log(this.banners);
        })
      }
    }
  }
</script>

<style scoped>
  .home-nav {
    background-color: var(--color-tint);
    color: #fff;
    /* background-color: red; */
  }
</style>