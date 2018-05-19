<template>
    <!-- 只需要一个最外层的包裹元素 -->
    <div>
        <div>
            <input  v-model="inputValue"/>
            <button @click="handleSubmit">提交</button>
        </div>
        <ul>
            <todo-item v-for="(item, index) of list" :key="index" :content="item" :index="index" @delete = "handleDelete"></todo-item>
        </ul>
    </div>
</template>

<script>
// 子组件引入
import TodoItem from './components/TodoItem.vue'
// 父组件
export default {
  // data: function(){
  //     return{

  //     }
  // }
  components: {
    'todo-item': TodoItem
  },
  data () {
    return {
      inputValue: '',
      list: []
    }
  },
  methods: {
    handleSubmit () {
      //  this.$data.list
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    handleDelete (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style>
</style>
