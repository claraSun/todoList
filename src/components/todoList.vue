<template>
  <div class="wrapper">
    
    <h2>Clara's todoList 共 {{todos.length}} 筆</h2>
    <el-input
      class="enteriput"
      placeholder="輸入待辦事項"
      v-model="needtodo"
      clearable
      @keyup.enter.native="enterHandler" />
    <ul>
      <li  v-for="(item,id) in todos" :key="id" :class="{ done: item.status }">
        <div v-show="!item.edit">{{item.text}}</div>
        <input class="edittext" v-show="item.edit" v-model="item.text">
        <div>
        <el-button icon="el-icon-check" circle @click="checkHandler(id)"></el-button>
        <el-button type="primary" icon="el-icon-edit" circle @click="editHandler(id)"></el-button>
        <el-button type="danger" icon="el-icon-delete" circle @click="deleteHandler(id)"></el-button>
        </div>
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  name: 'todoList',
  data() {
    return {
      currentPage1: 5,
      needtodo: '',
      todos: [
        {
          text: '餵貓',
          status: true,
          edit: false
        },
        {
          text: '買飯',
          status: false,
          edit: false
        },
        
      ]
    }
  },
  methods: {
    enterHandler() {
      if(this.needtodo) {
        this.todos.push(
          {
            text: this.needtodo,
            status: false,
            edit: false
          }
        )
        this.needtodo = ''
      }else {
        alert('請輸入文字')
      }
    },
    checkHandler(item) {
      this.todos[item].status = !this.todos[item].status
      
    },
    editHandler(item) {
      this.todos[item].edit = !this.todos[item].edit
    },
    deleteHandler(item) {
      this.todos.splice(item, 1)
    }
    
  }
}
</script>

<style scoped>
.wrapper{
  background: #fff;
  width: 60%;
  height: 100vh;
  min-height: 800px;
  margin: 20px auto;
  padding: 15px;
  position: relative;
  
}
.enteriput{
  font-size: 20px;
  height: 4rem;
  line-height: 4rem;
}
ul {
  list-style: none; 
  padding-left: 0;
}
li {
  font-size: 20px;
  height: 5rem;
  padding: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #DCDFE6;
}
.edittext {
  color: #ffffff;
  font-size: 20px;
  background: black;
  border: 0;
}
.done{
  text-decoration:line-through;
  
}
.done .el-button--default{
  background: #67c23a;
  color: white;
}
.block {
  padding: 15px;
}
</style>
