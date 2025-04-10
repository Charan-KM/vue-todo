<template lang="pug">
    div
      h1 Todo App
      input(v-model="newTodo", @keyup.enter="addTodo", placeholder="Add a new todo")
      ul
        li(v-for="(todo, index) in todos" :key="index")
          span {{ todo }}
          button(@click="removeTodo(index)") Delete
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: "",
        todos: [],
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim()) {
          this.todos.push(this.newTodo.trim());
          this.newTodo = "";
        }
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>
  input {
    padding: 5px;
    margin-right: 10px;
  }
  button {
    margin-left: 10px;
    padding: 5px;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: flex;
    justify-content: space-between;
    padding: 5px;
    border-bottom: 1px solid #ccc;
  }
  </style>  