<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="isCheck"/>
    </label>
    <span>
          <span>已完成{{finishCount}}件</span> / 总计 {{todos.length}} 件
        </span>
    <button class="btn btn-warning" @click="delHasFinsh()">清除已完成任务</button>
  </div>
</template>

<script>
  export default {
    name: "Footer",
    props:{
        todos:Array,
        delHasFinsh:Function,
        chooseAll:Function
    },
    computed:{
      finishCount(){
          return this.todos.reduce((total,item) => total + (item.finished ? 1 : 0),0)
      },
      isCheck:{
          get(){
              return this.finishCount == this.todos.length && this.todos.length > 0;
          },
          set(value){
             this.chooseAll(value);
          }
      }
    }
  }
</script>

<style scoped>
  /*尾部*/
  .todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
  }

  .todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
  }

  .todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
  }

  .todo-footer button {
    float: right;
    margin-top: 5px;
  }
</style>
