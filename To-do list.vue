<template>
  <div class="todo-app">
  <h1>Akshat's todo app</h1>
  <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
  <ul>
  <li v-for="(task, index) in tasks" :key="index">
  <input type="checkbox" v-model="task.completed">
  <span :class="{ completed: task.completed }">{{ task.text }}</span>
  <button @click="removeTask(index)">DELETE</button>
  </li>
  </ul>
  </div>
 </template>
  
 <script>
 export default {
  data() {
  return {
  newTask: '',
  tasks: []
  };
  },
  methods: {
  addTask() {
  if (this.newTask.trim() !== '') {
  this.tasks.push({
  text: this.newTask,
  completed: false
  });
  this.newTask = '';
  }
  },
  removeTask(index) {
  this.tasks.splice(index, 1);
  }
  }
 };
 </script>
  
 <style scoped>
 .todo-app {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
  font-family: Arial, sans-serif;
  color:gold
 }
  
 ul {
  list-style: none;
  padding: 2px;
 }
  
 li {
  display: flex;
  align-items: center;
  margin: 5px 0;
 }
  
 .completed {
  text-decoration: line-through;
  color: red;
 }
  
 button {
  margin-left: 10px;
  padding: 5px 10px;
  background-color: #f44336;
  border: none;
  color: white;
  cursor: pointer;
 }
 </style>