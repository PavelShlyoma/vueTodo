<script setup>
  import { ref,} from 'vue'

  const currentInput = ref({
    todoDate: "",
    todoTitle: "",
    todoBody: "",
    id: "",
  })

  const todos = ref([{
    id: "1",
    todoDate: "2025-12-31",
    todoTitle: "Новый год",
    todoBody: "Бугать",
  }])

  const addTodo = () => {
    currentInput.value.id = todos.value.length + 1;
    todos.value.push(currentInput.value);
    currentInput.value = {
      todoDate: "",
      todoTitle: "",
      todoBody: "",
      id: ""
    };
  }

</script>

<template>
  <form v-on:submit.prevent="addTodo" action="#">
    <input class="current-input" v-model="currentInput.todoDate" type="date" min="2025-08-13" placeholder="2025-08-13">
    <input class="current-input" v-model="currentInput.todoTitle" type="text" placeholder="Тема">
    <input class="current-input" v-model="currentInput.todoBody" type="text" placeholder="Описание задачи">
    <button class="current-btn">Добавить задачу</button>
  </form>

  <div class="todo">
    <div class="todo-items" v-for="(todo, index) in todos" :key="todo.id">
      <h2 class="todo-date">{{ todo.todoDate }}</h2>
      <div class="todo-item">
        <h3 class="todo-title">{{ todo.todoTitle }} :</h3>
        <p class="todo-text">{{ todo.todoBody }}</p>
      </div>
      <button class="delete-btn" @click="todos.splice(index, 1)">Закрыть задачу</button>
    </div>
  </div>
</template>

<style scoped>

.current-input {
  width: 100%;
  padding: 10px;
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 5px;
}

.current-btn {
  width: 100%;
  padding: 10px;
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
  background-color: #d64a0b;
  color: white;
}

.todo {
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 10px 0 20px;
}

.todo-items {
  display: flex;
  justify-content: center;
  flex-direction: column;
  margin: 15px 0 10px;
  padding: 10px 0 20px;
  -webkit-box-shadow: -17px -16px 36px -8px rgba(0, 0, 0, 0.11);
  -moz-box-shadow: -17px -16px 36px -8px rgba(0, 0, 0, 0.11);
  box-shadow: -17px -16px 36px -8px rgba(0, 0, 0, 0.11);
}

.todo-date {
  font-weight: bold;
  font-size: 20px;
  color: black;
  padding-bottom: 5px;
  text-align: center;
}

.todo-title {
  font-weight: bold;
  font-size: 24px;
  color: black;
  padding-bottom: 5px;
}

.todo-text {
  font-weight: 400;
  font-size: 18px;
  color: black;
  padding-bottom: 5px;
}

.todo-item {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}

.delete-btn {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  background-color: #d64a0b;
  color: white;
}

</style>