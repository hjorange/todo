<template>
  <header class="header">
    <h1>todos</h1>
    <input v-model="isall" id="toggle-all" class="toggle-all" type="checkbox" >
    <label for="toggle-all"></label>
    <input
      class="new-todo"
      placeholder="输入任务名称-回车确认"
      autofocus
      @keyup.enter="enter"
      v-model="task"
    />
  </header>
</template>

<script>
export default {
  props:['arr'],
  data(){
    return {
task:''
    }
  },
  methods:{
    enter(){
this.task.length?this.$emit('onenter',this.task):alert('数据不能为空')
this.task=''
    }
  },
  computed:{
    isall:{
      set(check){
this.arr.forEach(item=>item.isDone=check)
      },
   get(){return this.arr.every(item=>item.isDone)}   
    }
  }
 
}
</script>