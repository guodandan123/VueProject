<template>
  <div> 

<div class="header">
	<div>猫眼电影</div>
</div>
	<ul class="nav">
		<select name="" id=""><option value="">大连</option></select>
		<router-link class="left" activeClass="Tibbers" tag="li" to="/film/nowplaying">正在热映</router-link>
		<router-link class="rigth" activeClass="Tibbers" tag="li" to="/film/comingsoon">即将上映</router-link>
		<div class="search"><i class="iconfont icon-search"></i></div>
	</ul>
	

<router-view></router-view>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'film',
  data(){
  	return{
  		filmList:[]
  	}
  },

  mounted(){
  	axios.get('/ajax/movieOnInfoList?token=').then(res=>{
  	this.filmList=res.data.movieList;
  	console.log(res.data.movieList)
  })
  }
}
</script>

<style scoped>
.Tibbers{
	border-bottom: 3px solid #e54847;
	color: #e54847
}
.nav{
	font-weight: 700;
	display: flex;
width: 100%;
height:30px; 

}
.header{

	line-height: 50px;
	width: 100%;
	height: 50px;
	background:#e54847;
	position: relative;
	left: 0;
	top: 0;
	color: #fff;
	font-size:20px;
	text-align: center;
}
li{
	text-align: center;
	flex: 1;
	height:30px;
	line-height: 30px;
	list-style: none;
}
select{
	background: none;
	font-size: 14px;
	border:none;
}
div.search{
	margin-top: 3px;
	margin-right: 20px;
}
div i{
	color: #e54847;
	width: 20px;
	height: 20px;
	font-weight:bold;
}
</style>
