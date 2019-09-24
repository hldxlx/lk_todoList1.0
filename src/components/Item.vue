<template>
    <li
      @mouseenter="dealShow(true)"
      @mouseleave="dealShow(false)"
      :style="{background:bgColor}"
    >
      <label>
        <input type="checkbox" v-model="todo.finished">
      </label>
      <span>{{todo.title}}</span>
      <button v-show="isShowBtn" @click="delItem()">删除</button>
    </li>
</template>

<script>
  export default {
    name: "Item",
    props: {
      todo:Object,
      index:Number,
      delTodo:Function
    },
    data() {
      return {
        isShowBtn:false,
        bgColor:"#fff"
      }
    },
    methods: {
      dealShow(flag){
          this.isShowBtn = flag;
          flag ? this.bgColor = "#ddd" : this.bgColor = "#fff"
      },
      delItem(){
          this.delTodo(this.index);
      }
    }
  }
</script>

<style scoped>
  /*列表选项*/
  li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
  }

  li label {
    float: left;
    cursor: pointer;
  }

  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
  }

  li button {
    background-color: orangered;
    padding: 4px 10px;
    border-radius: 5px;
    color: #fff;
    border: none;
    float: right;
    margin-top: 3px;
    outline: none;
    cursor: pointer;
  }

  li:before {
    content: initial;
  }

  li:last-child {
    border-bottom: none;
  }
</style>
