<script>
// 声明式渲染，可以提高开发效率

// 在 script 中导出的内容，可以在 template 中使用
// .vue 就是一个组件
export default {
	data() {
		return {
			activeColor: 'red',
			fontSize: '50px',	
			backgroundColor: 'blue',
			objClass: {
				color:'red',
				fontSize:'50px', 
				'background-color': 'blue'
			},
			arrClass: {
				fontSize: '100px',
				border: "1px solid red",
			}
		}
	}
}
</script>

<template>
	<div>
		<!-- 第一种， 放置字符串 -->
		<p style="color: red;"> hello red</p>

		<!-- 第二种，放置对象 -->
		<p :style="{color:activeColor,fontSize:fontSize }"> hello color fontSize</p>
		<p :style="objClass"> hello color font-size</p>

		 <!-- 第三种，数组语法 -->
		<p :style="[arrClass]"></p>


	</div>
</template>

<style >

</style>
