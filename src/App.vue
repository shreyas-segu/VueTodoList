<template>
  <div>
    <Add @addTodoEvent="addTodo" />
    <TodoList :todos="todos" @deleteTodo="deleteTodo" />
  </div>
</template>

<script>
import Add from "./components/Add";
import TodoList from "./components/TodoList";

export default {
  components: {
    Add,
    TodoList
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo);
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    deleteTodo(id) {
      var todoArr = JSON.parse(localStorage.getItem("todos"));
      var index = todoArr
        .map(item => {
          return item.id;
        })
        .indexOf(id);
      todoArr.splice(index, 1);
      localStorage.setItem("todos", JSON.stringify(todoArr));
      this.todos = todoArr;
    }
  },
  created() {
    this.todos = JSON.parse(localStorage.getItem("todos"));
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
