<template>
	<div id="home">
		<nav-bar class="home-nav">
			<div slot="center">购物街</div>
		</nav-bar>
		<home-swiper :banners="banners"></home-swiper>
	</div>
</template>

<script>
	import NavBar from 'components/common/navbar/NavBar'
	import HomeSwiper from './childComps/HomeSwiper.vue'

	import {getHomeMultidata} from 'network/home.js'
	
  export default{
    name:"Home",
		components:{
			NavBar,
			HomeSwiper
		},
		data(){
			return{
				banners:[],
				recommends:[]
			}
		},
		created(){
			//1.请求多个数据
			getHomeMultidata().then(res=>{
				console.log(res);
				this.banners = res.data.banner.list;
				this.recommends = res.data.recommend.list;
			})
		}
  }
	console.log("go to home")
</script>

<style>
	.home-nav{
		background-color: var(--color-tint);
		color: white;
	}
</style>
