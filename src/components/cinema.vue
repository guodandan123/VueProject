<template>

<div>
<header> 
		
			<div class="cinema">影院</div>
			<div class="inp">
				  <i class="iconfont icon-plus-select-down"></i>
	 			<select name="" id=""><option value="">大连</option></select>
				<i class="iconfont icon-icon-" id="magnimier"></i>
				<input type="text" placeholder="搜影院" class="search">
				<ul class="qqq">
					<li @click="isShow=!isShow"><div class="ci">全城</div></li>
					<i id="on" class="iconfont icon-plus-select-down"></i>
					<li class="one"><div >品牌</div></li>
					<i id="tw" class="iconfont icon-plus-select-down"></i>
					<li><div  class="child">特色</div></li>
					<i id="sr" class="iconfont icon-plus-select-down"></i>
				</ul>
				<div  v-show="isShow" class="city">
					<div class=nav>
						<div :class="isact?'lef left':'left'" @click="isact=!isact">商区</div>
						<div class="right righ">地铁站</div>
					</div>
					<div class="nave">全部(65)</div>
					<ul class="ciy">
						<li>甘井子区(15)
						
							
						</li>
						<li>中山区(12)</li>
						<li>沙河口区(10)</li>
						<li>开发区(6)</li>
						<li>瓦房店市(5)</li>
						<li>金州区(4)</li>
						<li>普兰店市(4)</li>
						<li>庄河市(3)</li>
						<li>西岗区(3)</li>
						<li>旅顺口区(2)</li>
						<li>长海县(1)</li>
					</ul>
					</div>
					
				
			</div>
		
	</header>

	<div class="falls">
		<div class="list" v-for="datalist in cinemaList">
			<div class="h1">{{datalist.nm}}</div> 
			<span class="span">{{datalist.sellPrice}}<span>元起</span></span>
			<p>{{datalist.addr}}<div>{{datalist.distance}}</div></p>
			<div class="spanParent">
			
				<span v-if="datalist.tag.buyout" class="blu">改签</span>
				<span v-if="datalist.tag.cityCardTag" class="yellow">小吃</span>
				<span v-if="datalist.tag.deal" class="yellow">折扣卡</span>
				
				<span v-if="datalist.tag.halltype" class="blu">厅</span>
			</div>
		</div>
	</div></div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'cinema',
  data(){
	return {
		cinemaList:[],
		isShow:false,
		isact:0,
		
	}
  },
   components:{
		
  },
  mounted(){
  	axios.get('/ajax/cinemaList?day=2018-08-01&offset=0&limit=20&districtId=-1&lineId=-1&hallType=-1&brandId=-1&serviceId=-1&areaId=-1&stationId=-1&item=&updateShowDay=true&reqId=1533121602991&cityId=65').then(res=>{
  	this.cinemaList=res.data.cinemas;
  	//console.log(res.data.cinemas)
  })
  }
}
</script>

<style  scoped>
.qqq{
	display: flex;
}
.qqq li{
	height: 45px;
	line-height: 45px;
	flex: 1;
	text-align: center;
	list-style: none;
}
	header{
		width:100%;
		height:50px;
		background:#e54847;
		position: fixed;
		left: 0;
		top: 0;
		z-index: 10;
	}
	header .cinema{
		width:100%;
		height:50px;
		line-height: 50px;
		text-align: center;
		font-size: 20px;
		color:#fff;
	}
	header .inp{
		width: 100%;
		height: 80px;
		padding-top: 6px;
		background-color: #f5f5f5;
		position: relative;

	}
	header .inp i{
		font-size: 16px;
		color: #ccc;
	}
	header .inp span{
		margin-left: 15px;
		float: left;
		width: 40px;
		color: #666;
	}
	header .inp input{
		width:80%;
		height: 25px;
		margin-left: 10px;
		text-align: center;
		border:1px solid #e9e9e9;
		border-radius: 5px;
	}
	#magnimier{
		position: absolute;
		left: 165px;
		top: 11px;
		color: #b0b0b0;


	}
	header .qqq{
		width: 100%;
		height: 45px;
		background: #ffffff;
		margin-top: 6px;
		display: flex;
		font-size: 14px;
		border-bottom: 1px solid #dddddd;
		position: relative;
			i{
			position: absolute;

			}
			 #on{
				left: 85px;
				top: 15px;
			}
			#tw{
				right: 170px;
				top: 15px;
			}
			#sr{
				right: 35px;
				top: 15px;
			}

			 li{
				width: 34%;
				height: 45px;
				line-height: 45px;
				background: #fff;
				text-align: center;
				padding-left: 15px;
		
		}
	}

				.child{
					border-right: none;
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
	font-size:24px;
	text-align: center;
}
.falls{width: 95%;
		height: 120px;
		margin: 0 auto;
		background:#fff;                              
		margin-top: 50px;} 

.list{
margin-top: 10px;
	   border-bottom: 1px solid #ccc;
	   padding-bottom: 10px;}
.h1{font-size: 16px;
   display: inline-block;
				}
.span{font-size: 14px;
	  color: #f3645f;
	  margin-right: 50px}
.span span{font-size: 14px;
margin-right:-25px }

p{
  width:300px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow:ellipsis;
  font-size: 12px;
  margin-top: 5px;
  color: #a5a5a5;}
span{position: absolute;
	right: 0;
	width:50px;
				}


.spanParent span{	margin-top: 3px;
	margin-bottom: 3px;
	border:1px solid #57c0f8;
	border-radius: 2px;
	color:#57c0f8;
	font-size: 12px;
}

.blu{
	border:1px solid #57c0f8;
	background: #57c0f8;
	color: #b3e2fb;
	font-size: 12px;


	}
.last{
    font-size: 12px;
    color: #9f9f9f;
    	}

.city{
	position: fixed;
	left: 0;
	top:135px;
	background: #ccc;
	width:100%;
	height:100%;
	
}
.nav{
	width:100%;
	height:50px;
	background:#edc;
	text-align: center;
	line-height: 50px;

}
.left{
	width:50%;
	height: 100%;
	background:#edd;
	float: left;
}
.right{
	width:50%;
	height: 100%;
	background:#ecd;
	float: right;
}
.nave{
	width: 100%;
	height: 40px;
	display: block;
	line-height: 40px;
}
.ciy li{
	width:120px;
	height: 40px;
	line-height: 40px;
	background:#fff;

}
.lef{
	border-bottom: 1px solid red;
}
.righ{
	border-bottom: 1px solid red;

}
select{
	background: none;
	font-size: 14px;
	border:none;
}
</style>
