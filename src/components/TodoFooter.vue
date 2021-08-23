<template>
  <footer class="footer">
    <span class="todo-count">剩余<strong>数量：{{undone}}</strong></span>
    <ul class="filters">
      <li>
        <a @click="$emit('setactive','all')" :class="{selected:active==='all'}" href="javascript:;" >全部</a>
      </li>
      <li>
        <a @click="$emit('setactive','undone')" :class="{selected:active==='undone'}" href="javascript:;">未完成</a>
      </li>
      <li>
        <a @click="$emit('setactive','done')" :class="{selected:active==='done'}" href="javascript:;" >已完成</a>
      </li>
    </ul>
    <button class="clear-completed" @click="clear">清除已完成</button>
  </footer>
</template>

<script>
export default {
props:['arr','active'],
computed:{
  undone(){
    return this.arr.filter(item=>!item.isDone).length
  }
},
methods:{
  clear(){
    const undone=this.arr.filter(item=>!item.isDone)
    this.$emit('onclear',undone)
  }
}
}
</script>