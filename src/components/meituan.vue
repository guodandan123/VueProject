<template>
  <div> 

<div class="header">
	 <div>
          <form id="logupdetail"  >
            <input type="" name="" placeholder=" 账户/手机号/E-mail" class="username"><br>
            <input type="" name="" placeholder=" 请输入您的密码" class="password"><br>
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
	input.username{
		margin-top: 3px;
		height:40px;
		width:100%;
		border:0;
		border-bottom: 1px solid #ccc;
		border-top: 1px solid #ccc;
	}
	input.password{
		height:40px;
		width:100%;
		border:0;
		border-bottom: 1px solid #ccc;
		border-top: 1px solid #ccc;
	}
	button.btn{
		width:95%;
		height:50px;
		background-color: #df2d2d;
		color: white;
		font-size: 16px;
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
		display: block;
	}
	.find{
		float: right;
		margin-right: 10px;
		margin-top: 10px;
		color: #df2d2d;
		cursor: pointer;
		display: block;
	}
	span{
		font-size: 14px;
	}
	p{
		text-align: center;
	}
	p span{
		color: #df2d2d;
	}
</style>
