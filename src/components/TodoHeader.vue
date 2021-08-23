<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" >
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
  }
 
}
</script>