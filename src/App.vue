<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header :addTodo="addTodo"/>
       <List :todos="todos" :delTodo="delTodo"/>
      <Footer :todos="todos" :delHasFinsh="delHasFinsh" :chooseAll="chooseAll"/>
    </div>
  </div>
</template>

<script>
  // 1. 引入
  import Header from './components/Header.vue';
  import List from './components/List.vue';
  import Item from './components/Item.vue';
  import Footer from './components/Footer.vue';

  export default {
    name: "App",
    data(){
      return {
          todos:[
            {title:'篮球',finished:false},
            {title:'足球',finished:false},
            {title:'棒球',finished:false},
            {title:'排球',finished:true},
          ]
      }
    },
    // 2. 映射
    components:{
      Header,
      List,
      Item,
      Footer
    },
    methods:{
      // 插入一条记录
      addTodo(todo){
          this.todos.unshift(todo)
      },
      // 删除一条记录
      delTodo(index){
          this.todos.splice(index,1)
      },
      // 选中所有计划
      chooseAll(value){
          this.todos.forEach((todo) =>{
              todo.finished = value;
          })
      },
      //清除已完成
      delHasFinsh(){
          this.todos = this.todos.filter(todo => !todo.finished)
      }
    }
  }
</script>

<style scoped>
  /*主面板*/
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>
