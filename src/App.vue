<template>
  <div id="app">

    <div id="root">
      <div class="todo-container">
        <div class="todo-wrap">
          <MyHeader :addTodoItem="addTodoItem" />
          <MyList :todos="todos" :changeItem="changeItem" :deleteItem="deleteItem" />
          <MyFooter :todos="todos" :selectAll="selectAll" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MyFooter from './components/MyFooter.vue'
import MyHeader from './components/MyHeader.vue'
import MyList from './components/MyList.vue'


export default {
  name: 'App',
  components: {
    MyFooter,
    MyHeader,
    MyList
  },
  data() {
    return {
      todos: [
        { id: '0001', title: '吃饭', completed: true },
        { id: '0002', title: '睡觉', completed: false },
        { id: '0003', title: '抽烟', completed: false },
        { id: '0004', title: '学习', completed: true },
      ]
    }
  },
  methods: {
    addTodoItem(item) {
      if (item) {
        this.todos.unshift(item)
      }
    },
    changeItem(id) {
      console.log(id)
      for (const key in this.todos) {
        if (Object.hasOwnProperty.call(this.todos, key)) {
          const element = this.todos[key];
          if (element.id === id) {
            this.todos[key].completed = !this.todos[key].completed;
          }
        }
      }
    },
    deleteItem(id) {
      if (confirm('确定删除吗？')) {
        this.todos = this.todos.filter((todo) => {
          return todo.id !== id
        })
      }
    },
    selectAll(x) {
      this.todos.forEach((todo) => {
        return todo.completed = x
      });
    }
  }
}
</script>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

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
