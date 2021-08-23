<template>
  <ul class="todo-list">
    <!-- completed: 完成的类名 -->
    <li :class="{completed:item.isDone}" v-for="(item,index) in arr" :key="item.id">
      <div class="view">
        <input class="toggle" type="checkbox" v-model="item.isDone"/>
        <label>{{item.name}}</label>
        <button class="destroy" @click="btn(index)"></button>
      </div>
    </li>
  </ul>
  
</template>

<script>
export default {
  props:['arr'],
  methods:{
    btn(index){
   this.arr.splice(index,1)
    }
  }
}
</script>