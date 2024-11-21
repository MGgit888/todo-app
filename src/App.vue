<template>
    <div>
      <h1>To-Do List</h1>
      <p>Add an item in the box below to add an item to the list!</p>
      <input type="text" v-model="newTodo" @keyup.enter="addTodo">
      <ul>
        <li v-for="todo in todos" :key="todo.id">
          {{ todo.text }}
          <button @click="removeTodo(todo.id)">Remove</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: '',
        todos: [
          { id: 1, text: 'Learn Vue' },
          { id: 2, text: 'Build a To-Do App' }
        ]
      }
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim()) {
          this.todos.push({ id: Date.now(), text: this.newTodo });
          this.newTodo = '';
        }
      },
      removeTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id);
      }
    }
  }
  </script>