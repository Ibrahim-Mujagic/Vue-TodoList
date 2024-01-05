<script>
import TodoInputComponent from "./TodoInputComponent.vue";
import TodoItemComponent from "./TodoItemComponent.vue";
import todoThings from "../data/todoThings.js";
export default {
  name: "TodoCardComponent",
  components: {
    TodoInputComponent,
    TodoItemComponent,
  },
  data() {
    return {
      todoThings,
    };
  },
};
</script>

<template>
  <div class="todo-container">
    <TodoInputComponent />
    <div class="main-todolist">
      <TodoItemComponent
        v-for="(todoData, index) in todoThings"
        :key="index"
        :todoData="todoData"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.todo-container {
  height: 600px;
  width: 500px;
  border: 2px solid #85e89d;
  border-radius: 10px;
  overflow-y: auto;
  scrollbar-width: none;
  scrollbar-color: transparent transparent;

  &::-webkit-scrollbar {
    display: none;
  }
  .main-todolist {
    width: 100%;
    display: flex;
    flex-direction: column;
  }
}
</style>
