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
      errorMessage: "",
    };
  },
  methods: {
    getDataError(errorData) {
      this.errorMessage = errorData;
    },
  },
};
</script>

<template>
  <p v-if="errorMessage !== ''" class="errorMsg">{{ errorMessage }}</p>
  <div class="todo-container">
    <TodoInputComponent @notifyError="getDataError" />
    <div class="main-todolist">
      <TodoItemComponent
        v-for="(todoData, index) in todoThings"
        :key="index"
        :todoData="todoData"
        :todoItemIndex="index"
        @notifyError="getDataError"
      />
      <h2 v-if="todoThings.length === 0">Tutto Completato!!!😎​😁​</h2>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.errorMsg {
  color: crimson;
}
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
    height: calc(100% - 70px);
    width: 100%;
    display: flex;
    flex-direction: column;

    h2 {
      text-align: center;
      margin-top: 90px;
      color: #85e89d;
      text-decoration: underline;
      text-decoration-thickness: 2px;
    }
  }
}
</style>
