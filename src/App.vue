<template>
  <div class="todoapp">
<TodoHeader @onenter="downFn"/>
<TodoMain :arr="list"/>
<TodoFooter/>
  </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'
export default {
  components:{
TodoHeader,
TodoMain,
TodoFooter,
  },
  data () {
    return {
list: [
        { id: 100, name: "吃饭", isDone: true },
        { id: 201, name: "睡觉", isDone: false },
        { id: 103, name: "打豆豆", isDone: true },
      ],
    }
  },

  created () {

  },

  methods: {
downFn(taskname){
  const id=this.list.length?this.list[this.list.length-1].id+1:100
  this.list.push({
id:id,
name:taskname,
  })
}
  }
}
</script>

<style scoped>

</style>

