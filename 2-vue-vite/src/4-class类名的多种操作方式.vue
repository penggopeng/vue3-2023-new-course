<script>
// 声明式渲染，可以提高开发效率

// 在 script 中导出的内容，可以在 template 中使用
// .vue 就是一个组件
export default {
	data() {
		return {
			name: '小明',
			className: 'helloworld',
			isActive: true,
			error: {},
			classObj: {
				active: true,
				helloworld: true
			},
			activeClass: 'active'
		}
	},
	methods: {

	},
	computed: {
		classObjCom: function (){
			return {
				active: this.isActive && !this.error,
				helloworld: this.error,
			};
		}
	}
}
</script>

<template>
	<div>
		<h2>1. 对象的语法：</h2>
		<!-- 第一种，放置字符串 -->
		<p class="active"> hello string </p>

		<!-- 第二种，放置对象 -->
		<p :class="{active:isActive, helloworld:isActive}"> hello object</p>

		<!-- 添加按钮 -->
		<button @click="isActive = !isActive">改变 active</button>

		<p :class="{active:isActive, helloworld:isActive}"> hello object hello world</p>

		<!-- 和普通的类共存，不会冲突 -->
		<p :class="{active:isActive}" class="helloworld"> hello object hello depart</p>


		<!-- 直接通过传递 classObj 的方法传递类名称 -->
		<p :class="classObj">classObj 展示！！</p>

		<!-- 使用 computed  -->
		<p :class="classObjCom">computed 的控制 class 的名称</p>

		<h2>2. 数组的语法</h2> 
		<p :class="[className, activeClass]"> 数组的语法！！！！</p>

		<!-- 数组和对象结合的方式 -->
		<p :class="[message, {active: isActive}]"> 数组 & 对象 结合的方式  combine</p>
	</div>
</template>

<style scoped>

p {
	margin: 20px 0px;
}

.active{
	font-size: 50px;
	color: red;
}

.helloworld{
	background-color: rgb(174, 231, 204);
}

header {
	line-height: 1.5;
}

.logo {
	display: block;
	margin: 0 auto 2rem;
}

#d1 {
	color:red;
}

#d2 {
	color: blue;
}

@media (min-width: 1024px) {
	header {
		display: flex;
		place-items: center;
		padding-right: calc(var(--section-gap) / 2);
	}

	.logo {
		margin: 0 2rem 0 0;
	}

	header .wrapper {
		display: flex;
		place-items: flex-start;
		flex-wrap: wrap;
	}
}
</style>
