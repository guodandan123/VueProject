<template>
  <div> 

<div class="header">
	<router-link class="abc" to="/film/nowplaying"><i class="iconfont icon-fanhui"></i></router-link>
	<div>猫眼电影</div>
</div>
	<ul class="nav">
		<router-link class="left" activeClass="Tibbers" tag="li" to="/personal/meituan">美团账号登陆</router-link>
		<router-link class="rigth" activeClass="Tibbers" tag="li" to="/personal/cellphone">手机验证登陆</router-link>

	</ul>
	

<router-view></router-view>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'personal'
}
</script>

<style scoped>
	.Tibbers{
		border-bottom: 10px solid #df2d2d;
		color: #df2d2d;

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
	.abc{
		width: 20px;
		height: 20px;
		display: inline-block;
		float: left;
	}
	.abc i{
		font-size: 20px;
		margin-left:10px;
			 
	}
	i .iconfont{
		text-decoration:none;
		color: white;
	}
</style>
