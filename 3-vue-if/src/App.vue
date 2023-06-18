<script>
export default {
  data(){
    return {
      age: 18,
      sex: 'man'
    }
  }
}
</script>

<template>
  <div>
    <!-- v-if -->
    <p v-if="age > 18">我是成年人了</p>
    <p v-else-if="age == 18">今天已成年</p>
    <p v-if="age < 18">我还是个小朋友</p>

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

  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}
</style>
