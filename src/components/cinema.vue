<template>
	<div class="falls">
		<div class="header">
	<div>影院</div>
</div>
		<div class="list" v-for="datalist in cinemaList">
			<h3>{{datalist.nm}}</h3>
			<p>{{datalist.addr}}</p>
			<span v-if="datalist.tag.allowRefund">退</span>
			<span v-if="datalist.tag.buyout">改签</span>
			<span v-if="datalist.tag.cityCardTag">小吃</span>
			<span v-if="datalist.tag.deal">折扣卡</span>
			<span v-if="datalist.tag.endorse"></span>
			<span>卡</span>
			<span>开卡特惠，首单立减五元</span>


		</div>
	</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'cinema',
  data(){
	return {
		cinemaList:[]
	}
  },
   components:{
  	
  },
  mounted(){
  	axios.get('/ajax/cinemaList?day=2018-08-01&offset=0&limit=20&districtId=-1&lineId=-1&hallType=-1&brandId=-1&serviceId=-1&areaId=-1&stationId=-1&item=&updateShowDay=true&reqId=1533121602991&cityId=65').then(res=>{
  	this.cinemaList=res.data.cinemas;
  	console.log(res.data.cinemas)
  })
  }
}
</script>

<style  scoped>
	.falls{
		width: 100%;
		margin-top:50px; 

	}
ul,li{
	list-style: none;
}
html{
	margin:0;
	padding: 0;
}
.header{
	
	float: left;
	line-height: 50px;
	width: 100%;
	height: 50px;
	background:#e54847;
	position: fixed;
	left: 0;
	top: 0;
	color: #fff;
	font-size:24px;
	text-align: center;
}
</style>
