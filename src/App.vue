<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import TodoCardComponent from "./components/TodoCardComponent.vue";
export default {
  name: "App",
  components: {
    HeaderComponent,
    TodoCardComponent,
  },
};
</script>

<template>
  <HeaderComponent />
  <div class="container-general">
    <TodoCardComponent />
  </div>
</template>

<style lang="scss">
.container-general {
  height: calc(100vh - 80px);
  overflow-y: scroll;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
