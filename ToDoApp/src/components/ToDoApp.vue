
<template>
  <div class="todo-app custom-todo-app">
    <h1>Todo App</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" class="input-field" placeholder="Add a task">
    <ul>
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <span class="custom-todo-item">{{ todo.text }}</span>
        <button @click="deleteTodo(index)" class="custom-delete-button">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo });
        this.newTodo = '';
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>
.custom-todo-app {
  font-family: 'Verdana', sans-serif; /* Changed the font */
  max-width: 50%;
  max-height: 50%; /* Adjusted the max width */
  margin: 0 0;
  padding: 2rem; /* Increased padding */
  background-color: #6edda9; /* Changed the background color to gold */
  border-radius: 20px; /* Increased border radius */
  text-align: center;
}

h1 {
  font-size: 48px; /* Increased font size */
  margin-top: 10px;
  margin-bottom: 30px; /* Increased margin-bottom */
  color: #333;
}

ul {
  list-style-type: circle;
  padding: 1 rem;
 
}

.custom-todo-item { 
  margin-bottom: 20px; 
  font-size: 1.5rem; 
  margin-top: 1rem;
  margin-bottom: 1.7rem;
  margin-right: 3rem;
}

.custom-delete-button { /* Updated button class */
  background-color: #858180; /* Changed delete button background color to orange red */
  color: #fff;
  border: none;
  padding: 5px 9px; /* Adjusted button padding */
  cursor: pointer;
  font-size: 16px; /* Increased font size */
  margin-top: -1rem;
}

.custom-delete-button:hover {
  background-color: #CD5C5C; /* Changed delete button hover color to Indian red */
}
</style>