<script>

export default {
  props: ["todos"],
  data() {
    return {
    }
  },
  methods: {
  },
}

</script>

<template>
  <div class="wrapper">
    <div class="todo" v-for="(todo, index) in todos" :key="todo.id">
      <div :class="{ active: todo.completed }" class="todo-items">
        <div class="x-line"></div>
        <h2 class="todo-date">{{ todo.todoDate }}</h2>
        <div class="todo-item">
          <h3 class="todo-title">{{ todo.todoTitle }} :</h3>
          <p class="todo-text">{{ todo.todoBody }}</p>
        </div>
        <div class="btn-container">
          <button class="delete-btn" @click="todos.splice(index, 1)">Закрыть задачу</button>
          <button v-if="todo.completed" @click="todo.completed = false" class="delete-btn active">Продолжить выполнение</button>
          <button v-else class="delete-btn" @click="todo.completed = true">Выполнено</button>
          <button class="delete-btn">Доп кнопка</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

.wrapper {
  max-width: 550px;
  margin: 0 auto;
}

.btn-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
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
  transition: 0.5s ease-in-out;
}

.todo-items.active {
  position: relative;
  opacity: 0.5;
}

.todo-items.active .x-line {
  visibility: visible;
}

.x-line {
  width: 550px;
  height: 2px;
  background-color: white;
  position: absolute;
  transform: translateY(-28%);
  left: 0;
  top: 40%;
  visibility: hidden;
}

.x-line::before,
.x-line::after {
  width: 100%;
  height: 2px;
  content: "";
  transition: transform 0.3s;
  position: absolute;
  left: 0;
  background-color: black;
}

.todo-items.active .x-line::before {
  transform: translateY(-15px) rotate(-9deg);
  top: 15px;
}

.todo-items.active .x-line::after {
  transform: translateY(15px) rotate(9deg);
  top: -15px;
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
  display: inline-block;
  width: 100%;
  padding: 5px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  background-color: #EACDC2;
  color: white;
  border: none;
}

.delete-btn.active {
  background-color: #372549;
}

</style>