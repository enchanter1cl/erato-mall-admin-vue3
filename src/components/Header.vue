<!--Header.vue-->
<template>
  <div class="header">
    <div class="left">
      左
      <span>{{ state.name }}</span>
    </div>
    <div class="right">右</div>
  </div>
</template>

<script setup>
import {pathMap} from "@/utils";
import {reactive} from "vue";
import {useRouter} from "vue-router";

// 获取路由实例
const router = useRouter()
// 声明路由和 title 对应的键值对
//33章移入utils
// const pathMap = {
//   index: '首页',
//   add: '添加商品'
// }
const state = reactive({
  name: '首页state'
})
//监听路由变化方法 afterEach
router.afterEach((to) => {
  //console.log('to', to);
  //to 能获取到 router 相关信息
  const {id} = to.query
  state.name = pathMap[to.name]
})

</script>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped>
.header {
  height: 50px;
  border-bottom: 1px solid #e9e9e9;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}
</style>