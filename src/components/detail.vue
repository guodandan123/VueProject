<template>
	<div  v-if="filminfo">
		<div class="header">
			 <router-link tag="div" to="/film/nowplaying"><i class="iconfont icon-fanhui"></i>{{filminfo.nm}} </router-link>
		</div>
      	<div v-if="filminfo">
<ul class="detail">
	<li><img :src="filminfo.img" alt=""></li>
	<li>
	<ul class="right">
		<li class="name"><h3>{{filminfo.nm}}</h3></li>
		<li class="sc">{{filminfo.sc}}</li>
		<li class="star">主演:{{filminfo.star}}</li>
		<li class="star">{{filminfo.showInfo}}</li>
		<li class="star">{{filminfo.pubDesc}}</li>
		<li class="star">地区{{filminfo.src}}</li>
	</ul>
	</li>
</ul>
	</div><br><br><br><br><br><br><br>
	<p class="intr">剧情简介：</p>
	<p class="p">{{filminfo.dra}}</p>



	<div class="falls">
		<p class="intr">上映地点：</p>
		<div class="list" v-for="datalist in cinemaList">
			<div class="h1">{{datalist.nm}}<span class="num">{{datalist.sellPrice}}元</span></div>
		
			<div class="addr">{{datalist.addr}}</div>
			<button class="one">退</button>
			<button class="one">改签</button>
			<button class="two">小吃</button>
			<button class="two">折扣卡</button>
			<div class="dis">{{datalist.distance}}</div>
			<br>
			<div class="spanParent">
			<button class="card">卡</button><div class="cardInfo">{{datalist.promotion.cardPromotionTag}}</div>
			</div>
	
		</div>
	</div>
</div>
</template>

<script>
import axios from "axios";
import router from "../router"
	export default {
		name:"detail",
		data(){
			return {
				cinemaList:[],
				filminfo:null,
				filterCinemas: [],
				filterdistrict:[]
			}
		},

		mounted(){
			//页面加载完 ，接受路由参数
			//console.log(this.$route.params.Tibbersid);
			//ajax请求数据
				axios.get('/ajax/cinemaList?day=2018-08-01&offset=0&limit=20&districtId=-1&lineId=-1&hallType=-1&brandId=-1&serviceId=-1&areaId=-1&stationId=-1&item=&updateShowDay=true&reqId=1533121602991&cityId=65').then(res=>{
  	this.cinemaList=res.data.cinemas;
  //	console.log(res.data.cinemas)
  })

			axios.get(`/ajax/detailmovie?movieId=${this.$route.params.Tibbersid}`).then(res=>{
				// console.log(res.data);
				this.filminfo = res.data.detailMovie//
				//console.log(this.filminfo.nm);
				this.filminfo.img=this.filminfo.img.slice(0,22)+ "170.230" + this.filminfo.img.slice(25)
				//this.$store.dispatch("mytitleAction",this.filminfo.nm)
				//dispatch("对应哪个action？"，传的值);
			}),
			axios.get(`/ajax/filterCinemas?movieId=${this.$route.params.Tibbersid}`).then(res=>{
  				this.filterCinemas=res.data.brand.subItems;
  				this.filterdistrict=res.data.district.subItems;

  				//console.log(res.data.brand.subItems)
  				//console.log(res.data.district.subItems)
  				
  })
		}
	}
</script>

<style scoped>
h4{
	display: inline-block;
}

.falls{
	width: 95%;
	height: 120px;
	background:#fff;                              
	margin-top: 20px;
	} 

.list{
	margin-left: 10px;
	margin-top: 20px;
	 border-bottom: 1px solid #ccc;
	 padding-bottom: 20px;
	 height: 90px;
	}
.h1{
	font-size: 16px;
	font-weight: 600;
   display: inline-block;
				}
.span{
	font-size: 14px;
	color: #f3645f;
	margin-right: 50px;
}
p.intr{
	text-indent:10px;
	font-weight: bold;
	line-height: 24px;
}
span{position: absolute;
	right: 0;
	width:50px;
}
.spanParent span{	margin-top: 3px;
	margin-bottom: 3px;
	border:1px solid #57c0f8;
	border-radius: 2px;
	color:#57c0f8;
	font-size: 10px;
}

.detail{
	margin-left: 20px
}
.detail img{
	margin:10px 0;
}
.cinemalist{
	padding-top: 20px;
	margin-left: 20px;
}

.header i{
	float: left;
	font-size: 24px;
	margin-left: 10px;
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
.p{
	color: #333;
	margin-left: 10px;
	margin-right: 10px;
	text-indent: 20px;
}

li{list-style: none;}
img{
	float: left;
	height: 114px
}
.sc{
	font-weight: 600;
	color: #ffcc00;
	font-size: 18px;
}
.star{
	overflow: hidden;
	width: 220px;
}
.right{
	padding-left: 30px;
	float: left;
	overflow: hidden;
	height: 114px;
	margin-top: 10px;
}
.list{
	border-bottom: 1px solid #eee;
}
.addr{
	font-size: 14px;
	color: #999;
	line-height: 20px;
}
.dis{
	float: right;
	margin-bottom: 50px;
}
.one{
	border:none;
	border:1px solid #589daf;
	background: white;
	color: #589daf;
}
.two{
	border:none;
	border:1px solid #ff9900;
	background: white;
	color: #ff9900;
}
.card{
	width: 15px;
	height: 15px;
	border:none;
	background: #57c0f8;
	color: white;

}
.cardInfo{
	font-size: 14px;
	display: inline-block;
	color: #999999;
	line-height: 28px;
}
.num{
	color: #f2544f;
}

</style>
