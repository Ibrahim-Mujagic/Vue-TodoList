<script>
export default {
  name: "TodoItemComponent",
  props: {
    todoData: Object,
  },
};
</script>

<template>
  <div class="todo-item">
    <p>{{ todoData.todoThing }}</p>
    <div class="todo-close">
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
  &.done {
    text-decoration: line-through;
  }

  .todo-close {
    color: crimson;
    cursor: pointer;
  }
}
</style>
