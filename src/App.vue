<template>
  <div id="app">
    <h1>My To-Do Lists</h1>
    <input
      v-model="newTodo"
      @keyup.enter="addTodo"
      placeholder="Add a new task"
    />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <span :class="{ completed: todo.completed }" @click="toggleTodo(index)">
          {{ todo.text }}
        </span>
        <button @click="removeTodo(index)">X</button>
      </li>
    </ul>
  </div>
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
      if (this.newTodo.trim() !== "") {
        this.todos.push({
          text: this.newTodo,
          completed: false,
        });
        this.newTodo = "";
      }
    },
    toggleTodo(index) {
      this.todos[index].completed = !this.todos[index].completed;
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}

.completed {
  text-decoration: line-through;
}

input {
  padding: 10px;
  font-size: 16px;
}

button {
  margin-left: 10px;
  background-color: red;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: darkred;
}
</style>
