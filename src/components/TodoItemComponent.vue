<script>
import todoThings from "../data/todoThings";
export default {
  name: "TodoItemComponent",
  props: {
    todoData: Object,
    todoItemIndex: Number,
  },
  data() {
    return {
      todoThings,
      errorOutput: "",
    };
  },
  methods: {
    deleteTodoItem() {
      if (this.todoThings[this.todoItemIndex].isDone === true) {
        this.todoThings.splice(this.todoItemIndex, 1);
        this.$emit("notifyError", (this.errorOutput = ""));
      } else {
        this.errorOutput =
          "Devi selezionare come fatto l'elemento prima di canellarlo";
        this.$emit("notifyError", this.errorOutput);
      }
    },
  },
};
</script>

<template>
  <div @click="todoData.isDone = !todoData.isDone" class="todo-item">
    <p :class="todoData.isDone ? 'completed' : 'notCompleted'">
      {{ todoData.todoThing }}
    </p>
    <div @click.stop="deleteTodoItem()" class="todo-close">
      <i class="fa-solid fa-x"></i>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.todo-item {
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px;
  border-bottom: 2px solid #85e89d;
  p {
    cursor: pointer;
  }
  p.completed {
    text-decoration: line-through;
    cursor: pointer;
  }

  .todo-close {
    color: crimson;
    cursor: pointer;
    padding: 5px;
  }
}
</style>
