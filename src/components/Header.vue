<template>
  <div class="header">
    <div class="left">
        <span style="font-size:20px">{{name}}</span>
    </div>
    <div class="right">右</div>
  </div>
</template>
<script>
import { defineComponent,reactive, toRefs } from 'vue' 
import { useRouter} from 'vue-router'


export default defineComponent({
  name: "Header",
  setup() {
      const router = useRouter()
      const pathMap = {
          index: '首页',
          add: '添加商品'
      }
      const state = reactive({
          name: '首页'
      })
      router.afterEach((to) => {
          console.log('to',to)
          const {id} = to.query
          state.name = pathMap[to.name]
      })
      return {
          ...toRefs(state)
      }
  },
});
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
