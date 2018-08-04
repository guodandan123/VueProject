<template>
  <div> 
  
  <ul>
    <router-link activeClass="Tibbers" tag="li" to="/film/nowplaying">
     <div><i class="iconfont icon-dianyingyuan"></i>
    </div><span >电影</span>
    </router-link>
    <router-link activeClass="Tibbers" tag="li" to="/cinema">
    <div><i class="iconfont icon-yingyuana"></i>
    </div><span >影院</span>
    </router-link>
    <router-link activeClass="Tibbers" tag="li" to="/personal/meituan">
    <div> <i class="iconfont icon-yonghu"></i>
   </div> <span >我的</span>
    </router-link>

  </ul>
  </div>
</template>

<script>

export default {
  name: 'navbar',
  data(){
  	return{}
  }
}
</script>

<style scoped>
span{

  text-align: center;
  display:block;
  font-size: 12px;
}

ul{
  background: #fff;
  z-index: 999;
  /*padding-top: 5px; */
  padding-bottom:5px; 
  border-top: 1px solid #ccc;
  position: fixed;
  bottom:0px;
  left: 0;
  width: 100%;
  height: 50px;
}
  ul li div{

     width:100%;
     height: 36px; 
     display: flex;
  }
ul li{
 
  text-align: center;
  float: left;
  list-style: none;
  width: 33.3%;
  height: 48px;
  position: relative;}
 
  i{
    margin:auto;
    display: block;
    height: 25px;
    width: 25px;
    font-size: 24px
  }
.Tibbers{
  color: red
}

</style>

