<script>
import TodoList from "@/component/TodoList.vue";

export default {
  components: {
    TodoList,
  },

  data() {
    return {
      currentInput: {
        todoDate: "",
        todoTitle: "",
        todoBody: "",
        id: "",
      },
      todos: [{
          id: "1",
          todoDate: "2025-12-31",
          todoTitle: "Новый год",
          todoBody: "Бугать",
          completed: false,
        }]
      }
    },
  methods: {
    addTodo() {
      this.currentInput.id = this.todos.length + 1;
      this.todos.push(this.currentInput);
      this.currentInput = {
        todoDate: "",
        todoTitle: "",
        todoBody: "",
        id: ""
      };

    }
  },
}

</script>

<template>
  <div class="wrapper">
    <form v-on:submit.prevent="addTodo" action="#">
      <input class="current-input" v-model="currentInput.todoDate" type="date" min="2025-08-13" placeholder="2025-08-13">
      <input class="current-input" v-model="currentInput.todoTitle" type="text" placeholder="Тема">
      <input class="current-input" v-model="currentInput.todoBody" type="text" placeholder="Описание задачи">
      <button type="submit" class="current-btn">Добавить задачу</button>
    </form>
    <todo-list :todos="todos" />
  </div>
</template>

<style scoped>

.wrapper {
  max-width: 550px;
  margin: 0 auto;
}

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

</style>