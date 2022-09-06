<template>
  <div>
    <h1>App根组件</h1>
    <hr>
    <todo-input @add="onAddNewTask"></todo-input>

    <todo-list :list="tasklist" class="mt-2"></todo-list>
    <todo-button v-model:active="activeBtnIndex"></todo-button>

  </div>
</template>

<script>
import TodoList from './components/todoList.vue'
import TodoInput from './components/todo-input/TodoInput.vue'
import TodoButton from './components/todo-button/TodoButton.vue'
export default {
  name: 'MyApp',
 
  data(){
    return{
      todolist:[
        // {id:1,task:'周一9点',done:false},
        // {id:2,task:'周一晚9点',done:false},
        // {id:3,task:'周准备',done:true},
      
      ],
      // 下一个可用的ID值
      nextId:4,
      activeBtnIndex:0
    }
  },
  methods:{
    // todoInput组件add事件的处理函数
    onAddNewTask(taskname){
      // console.log(taskname);
      // 向任务列表中新增任务信息
      this.todolist.push({
        id:this.nextId,
        task:taskname,
        done:false,
      })
      this.nextId++
    }
  },
  // 注册私有组件
  components:{
    TodoList,TodoInput,TodoButton,
  },
  computed:{
    tasklist(){
      switch(this.activeBtnIndex){
        // 0全部
        case 0:
          return this.todolist
          // 1 已完成
        case 1:
          return this.todolist.filter(x=>x.done)
        // 2 未完成
          case 2:
          return this.todolist.filter(x=>!x.done)
      }
    }

  }
}
</script>
<style lang="less" scoped>

</style>
