<script>
export default {
  data(){
    return {
      age: 18,
      sex: 'man',
      isShow: true,
    }
  }
}
</script>

<template>
  <div>
    <!-- v-if -->
    <p v-if="age > 18">我是成年人了</p>
    <p v-else-if="age == 18">今天已成年</p>
    <p v-if="age < 18">我还是个小朋友</p>``

    <!-- template 元素上使用 v-if 条件渲染分组 -->
    <template v-if="age < 15">
      <p>您好</p>
      <p>您好</p>
      <p>您好</p>
      <p>您好</p>
      <p>您好</p>
    </template>


    <!-- v-show  -->
    <p v-show="sex ==='man'">男生</p>
    <p v-show="sex ==='woman'">女生</p>


    <!-- v-show 只是简单的切换元素的 display css property， 带有  v-show 的元素始终会被渲染并保留在 DOM 中 -->
    <!-- v-if 只有后面 false, 对应的元素及其子元素都不会被渲染，控制 dom 元素的创建与销毁，运行条件很少改变的， 一次性的 -->
    <h2 v-if="isShow">标题内容1 v-if </h2>
    <h2 v-show="!isShow">标题内容2 v-show </h2>

    <button @click="isShow=!isShow">改变 isShow</button>

  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}
</style>
