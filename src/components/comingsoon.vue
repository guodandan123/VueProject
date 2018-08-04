<template>
  <div> 
	
<swipe class="my-swipe">
  	<swipe-item class="slide1" v-for="datalist in loopList" :key="datalist.id">
  	<ul>
  		<li><img :src="datalist.img" alt=""></li>	
	</ul>
  </swipe-item>
</swipe>


	<ul class="list" v-for="datalist in comingList"   @click="handleClick(datalist.id)">
	<li><img :src="datalist.img" alt=""></li>
<li>	<ul class="right">
		<li class="name"><h3>{{datalist.nm}}</h3></li>
		<li class="sc">评分:{{datalist.sc}}</li>
		<li class="star">主演:{{datalist.star}}</li>
		<li class="star">{{datalist.showInfo}}</li>

	</ul>
		<button :class="(datalist.showst=='4')?'blue':'yellow'"><span>{{datalist.showst=='4'?bbb:aaa}}</span></button> 
		<!-- <button>{{datalist.globalReleased}}</button> -->
</li>
</ul>

  </div>
</template>

<script>
require('vue-swipe/dist/vue-swipe.css');
import { Swipe, SwipeItem } from 'vue-swipe';
import axios from 'axios'
import router from "../router"
export default {
  name: 'App',
  data(){
  	return{
  		comingList:[],
  		loopList:[],
  		aaa:'想看',
  		bbb:'预售'
  	}
  },
  components:{

  	Swipe, SwipeItem

  },

   methods:{	
  	handleClick(data){
				// console.log(data)
				router.push(`/detail/${data}`); // /detail/222
			}

  },
   mounted(){
  	axios.get('/ajax/comingList?ci=65&token=&limit=10').then(res=>{
  	this.comingList=res.data.coming;
  //	console.log(res.data.coming);
  	for(var i =0;i<this.comingList.length;i++){
		this.comingList[i].img=this.comingList[i].img.slice(0,22)+ "170.230" + this.comingList[i].img.slice(25)}
	 })	

	axios.get('/ajax/mostExpected?ci=65&limit=10&offset=0&token=').then(res=>{
  	this.loopList=res.data.coming;
  	console.log(res.data.coming);
  	for(var i =0;i<this.loopList.length;i++){
		this.loopList[i].img=this.loopList[i].img.slice(0,22)+ "170.230" + this.loopList[i].img.slice(25)}
	 })			
  }

}
</script>

<style scoped>
.my-swipe{padding:5px 0;position: relative;}
.my-swipe img{
	/*margin-left: 40%;*/
	/*margin: auto;*/
	position: absolute;
	left: 0;
	top: 0;
	right: 0;
	bottom: 0;
	margin: auto;
}
.my-swipe {
  height:115px;
  /*color: #fff;*/
  font-size: 30px;
  text-align: center;
  margin: 0 auto;
}
.my-swipe ul{
	margin:auto;
}
.header{
	
	float: left;
	line-height: 50px;
	width: 100%;
	height: 50px;
	background:#e54847;
	position: relative;
	left: 0;
	top: 0;
	color: #fff;
	font-size:24px;
	text-align: center;
}
div{
	margin-bottom:50px;
}

li{list-style: none;}
img{
	float: left;
	height: 114px
}
.star{
	overflow: hidden;
	width: 220px;
}
.header{
	
	float: left;
	line-height: 50px;
	width: 100%;
	height: 50px;
	background:#e54847;
	position: relative;
	left: 0;
	top: 0;
	color: #fff;
	font-size:24px;
	text-align: center;
}


.list{	
	border-bottom: 1px solid #eee;
	height: 114px;
	padding:10px;
	font-size: 14px;
	line-height: 25px;
}
.right{
	padding-top:10px;
	padding-left:20px;
	float: left;
	overflow: hidden;
}
.list .name{

}
button{
	width: 50px;
	height: 30px;
	margin-top: 50px;
	float: right;
	border:none;
	color:white;
	border-radius: 3px;
	cursor: pointer;
}
.yellow{
	background: #faaf00;
}
.blue{
	background: #3c9fe6;
}
</style>
