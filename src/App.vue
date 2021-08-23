<template>
  <div class="todoapp">
<TodoHeader @onenter="downFn" :arr="list"/>
<TodoMain :arr="newlist" @delitem="delitem"/>
<TodoFooter :arr="list" @onclear="onclear" :active="isActive"
@setactive="setactive"/>
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
      isActive:'',
      list: JSON.parse(localStorage.getItem('list'))||[]
    }
  },
//已完成未完成全部渲染页面
 computed:{
   newlist(){
     if(this.isActive==='undone'){
       return this.list.filter(item=>!item.isDone)
     }else if(this.isActive==='done'){
        return this.list.filter(item=>item.isDone)
     }return this.list

   }
 },

watch:{
list:{
deep:true,
handler(){
  localStorage.setItem('list',JSON.stringify(this.list))
}
}
},
  methods: {
    //添加
downFn(taskname){
  const id=this.list.length?this.list[this.list.length-1].id+1:100
 const flag= this.list.some(item=>item.name===taskname)
 flag?alert('名字重复'):
  this.list.push({
id,
name:taskname,
  })
},
//清除已完成
onclear(undone){
this.list=undone
},
setactive(active){
this.isActive=active
},
//删除
delitem(id){
  const index=this.list.findIndex(item=>item.id===id)
  this.list.splice(index,1)
}
  }
}
</script>

<style scoped>

</style>

