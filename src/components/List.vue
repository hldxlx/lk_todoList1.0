<template>
  <ul class="todo-main">
      <Item v-for="(todo,index) in todos"
            :todo="todo"
            :key="index"
            :index="index"
            :delTodo="delTodo"
      />
  </ul>
</template>

<script>
    import Item from './Item.vue'
    export default{
        name:"List",
         props:{
           todos:Array,
           delTodo:Function
         },
        data(){
          return {

          }
        },
        components:{
          Item
        }
    }
</script>

<style scoped>
  /*列表*/
  .todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
  }
</style>
