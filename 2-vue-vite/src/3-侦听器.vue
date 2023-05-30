<script>
// 声明式渲染，可以提高开发效率


// 在 script 中导出的内容，可以在 template 中使用
// .vue 就是一个组件
export default {
	data() {
		return {
			question:'',
			answer: 'Questions usually contain a question mark . ;-)',
			test_input: 'hello world!',
			user: {
				name: '张三',
				age: 18,
				sex: '男'
			}
		}
	},
	methods: {
		getAnswer: function () {
			this. answer = 'Thinking...';
			axios
				.get('https//yesno.wtf/api')
				.then(response => {
					this.answer = response.data.answer
				})
				.catch(error => {
					this.answer = 'Error! Could not reach the API.' + error
				})
			
		}
	},
	watch: {
		// 监听数据的变化
		// 监听我的 message 有没有发生变化
		message: function (newValue, oldValue) {
			console.log(newValue);
			console.log(oldValue);

			// 执行异步操作，或者一些复杂的额逻辑代码
		},
		question: function (newQuestion, oldQuestion) {
			if (newQuestion.indexof('?') > -1) {
				this.getAnswer();
			}
		},
		// test_input: function(newInput, oldInput) {
		// 	console.log(newInput);
		// 	console.log(oldInput);
			
		// 	if (newInput.length < 5 || newInput.length > 10) {
		// 		console.log('输入框中的内容长度不能小于 5，或者大于 10 字符');
		// 	}
		// },
		// 监听的另一种写法， watch 的深度监听

		test_input: {
			immediate: true, // 初始化的时候调用函数
			handler: function (newInput, oldInput) {
				console.log(newInput);
				console.log(oldInput);
				
				if (newInput.length < 5 || newInput.length > 10) {
					console.log('输入框中的内容长度不能小于 5，或者大于 10 字符');
				}
			}
		},
		// watch 监听不到 对象的属性的变更。
		// 如果想要监听到对象属性的变化，需要用到深度监听。
		// user: {
		// 	handler: function (newValue) {

		// 	},
		// 	deep: true, // 表示是否深度监听，侦听器会一层层的向下遍历，对对象的每个属性进行侦听，但是这样做比较浪费资源
		// }

		"user.name": {
			handler: function(newValue) {
				console.log(newValue);
			},
			deep: true,
		}
	}
}
</script>

<template>
	<div>
		<br>
		<p>getter 方法调用</p>
		<p>{{reverseFully}}</p>


		<h2>改变</h2>
		<button @click="reverseFully='你好'">改变reverseFully</button>


		<h2>输入框的内容</h2>
		<input type="text" v-model="test_input">


		<p>{{user.name}}</p>
		<button @click="user.name = '李四'">改变对象名称</button>
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
