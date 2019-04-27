<template>
  <div class="hello">
    <input type="text" v-model="todoData">
    <button @click="getTodoList()">添加</button>
    <hr>
        <!-- 未完成 -->
    <h1>未完成</h1>
    <ul>
      <li v-for="(item,index) in list" v-if="!item.checked">
        <input type="checkbox" v-model="item.checked">
        {{item.title }}
        <button @click="deleteTodo(index)">刪除</button>
      </li>
    </ul>
    <hr>
    <!-- 已完成 -->
    <h1>已完成</h1>
    <ul>
      <li v-for="(item,index) in list" v-if="item.checked">
        <input type="checkbox" v-model="item.checked">{{item.title}}<button @click="deleteTodo(index)">刪除</button></li>
    </ul>
    <hr>

  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      todoData: "",
      list:[]
      
    };
  },
  methods: {
    getTodoList() {
      this.list.push({'title':this.todoData, checked:false});
      this.todoData = "";
    },
    deleteTodo(key) {
      this.list.splice(key,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* h1, h2 {
  font-weight: normal;
}
ul {  
  list-style-type: none;
  padding: 0;
}
li{
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */
</style>
