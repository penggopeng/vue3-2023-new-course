<script>
// 声明式渲染，可以提高开发效率


// 在 script 中导出的内容，可以在 template 中使用
// .vue 就是一个组件
export default {
	data() {
		return {
			num: 0,
			uname: "张三",
			msg: '<h1>你好</h1>',
			dynamicId: 'd2',
			url:'https://cdn.learnku.com/uploads/avatars/29783_1583913079.jpg!/both/100x100',
			timestamp: 0,
			message: 'flim heritage',
		}
	},
	computed:{ // 计算属性，只要依赖值不变，那么就不会重新计算。它会有缓存，只要 message 值不变，computed 就执行一次，其它的走缓存
		// 计算属性 : 计算属性将基于他们响应依赖关系缓存，提高性能
		// 简写的方式
		reveseMsg: function(){
			return this.message.split('').reverse().join('')
		},

		// 完整的方式，赋值一个对象
		// 每一个计算属性中，都一个  setter 和 getter 
		// 完整的写法
		// 计算属性一般没有 set 方法
		reverseFully:{
			get: function() {
				return this.message.split('').reverse().join('');
			},
			set: function(newValue) {
				console.log(newValue);
				this.message = newValue;
			}
		}
	},
	methods: {
		// 给 vue 定义方法
		changeUname: function () {
			// this 指向 vue 实例
			this.uname = '李四';
		},
		changeColor: function () {
			this.dynamicId = 'd1';
		}
	}
}
</script>

<template>
	<!-- 组件实例的所有 property 无论如何定义，都可以在组件中的模版中访问 -->
	<header>
		<img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
	</header>

	<div>
		<p>{{num}}</p>
		<p>{{uname}}</p>

		<p v-once>{{uname}}</p>
		<button @click="changeUname">改变名字</button>

		<p>{{msg}}</p>
		<!-- v-html 让内容可以以，Html 的形式进行显示。 -->
		<p v-html="msg"></p>


		<!-- v-bind: 绑定属性的内容，而不是更改了这个属性。 动态的绑定了属性的内容，而不是更改了这个属性 -->
		<p v-bind:id="dynamicId" > attribute 属性修噶不能使用， mustache 语法，{}  可以使用 v-bind: 来进行修改！！ </p>
		<img v-bind:src="url" alt="litter card">
		<p>
			<button @click="changeColor">改变颜色</button>
		</p>


		<!-- 使用 javascript 表达式 -->
		<p>{{num + 1}}</p>
		<p>{{uname.split('').reverse().join('')}}</p>
		<p v-bind:id="`d${num+1}`" > attribute 属性修噶不能使用， mustache 语法，{}  可以使用 v-bind: 来进行修改！！ </p>
	</div>
</template>

<style scoped>
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
