<template>
  <div id="home">
      <nav-bar class="home-nav">
          <div slot="center">购物街</div>
      </nav-bar>
      <h2>主页</h2>
  </div>
</template>

<script>
import NavBar from '@/components/common/navbar/NavBar'
import {getHomeMultidata} from '../../network/home'

export default {
  name:"Home",
  data: () => ({
      banner:[],
      recommends:[]
  }),
  components:{
      NavBar
  },
  methods: {

  },
  created(){
    //   1、请求我们多个数据
    getHomeMultidata().then(res=>{
        console.log(res);
       this.banner=res.data.banner;
       this.recommends=res.data.recommend.list;
    });
  },
  mounted () {

  }
}
</script>

<style>
    .home-nav{
        background-color: var(--color-tint);
        color: #fff;
    }
</style>