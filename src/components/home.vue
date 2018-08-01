<template>
  <div> 
  home
	<ul>	<li><div>大连</div></li>
			<router-link to="/file/nowplaying" activeClass="active" tag="li">正在热映</router-link>
			<router-link to="/file/comingsoon" activeClass="active" tag="li">即将热映</router-link>
			<li><span>搜索</span></li>
		</ul>


  </div>
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>

</style>
