<template>
  <div> 
<div>
	<div>
        <form>
      <input type="" name="" placeholder=" 请输入手机号" class="tel"><button>获取验证码</button>
      <input type="" name="" placeholder=" 请输入短信验证码" class="msg">
      </form>
     <center> <button class="btn">登录</button></center>

      </div> 
       <span class="reg">立即注册</span>
       <span class="find">找回密码</span>
       <br>
       <br>
       <p>
       		&copy;猫眼电影 客服电话：<span>4006705335</span>
       </p>
</div> 
<router-view></router-view>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'film'
}
</script>

<style scoped>
	input{
		/*padding-left: 5px;*/
	}
	input.tel{
		margin-top: 3px;
		position: relative;
		height:40px;
		width:100%;
		border:none;
		border-bottom: 1px solid #ccc;
		border-top: 1px solid #ccc;
	}
	input.msg{
		height:40px;
		width:100%;
		border:none;
		border-bottom: 1px solid #ccc;
		border-top: 1px solid #ccc;
	}
	button{
		position: absolute;
		right: 0;
		width: 18%;
		height: 30px;
		margin: 10px;
		border:none;
		border-radius: 3px;
		color: #aaa;
	}
	button.btn{
		font-size: 16px;
		width:95%;
		height:50px;
		background-color: #ccc;
		/*background-color: #df2d2d;*/
		color: white;
		border:none;
		margin-top: 15px;
		margin-left: 10px;
		text-align: center;
		border-radius: 5px;
	}
	span.reg{
		float: left;
		margin-left: 10px;
		margin-top: 10px;
		color: #df2d2d;
		cursor: pointer;
		margin-top:75px;
	}
	span.find{
		float: right;
		margin-right: 10px;
		margin-top: 10px;
		color: #df2d2d;
		cursor: pointer;
		margin-top:75px;
	}
	span{
		font-size: 14px;
	}
	p{
		text-align: center;
		margin-top:65px;
	}
	p span{
		color: #df2d2d;
	}

</style>
