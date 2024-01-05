<script>
import todoThings from "../data/todoThings";
export default {
  name: "TodoInputComponent",
  data() {
    return {
      todoThings,
      newTodoThing: "",
      isNewTodoIncluded: false,
      errorOutput: "",
    };
  },
  methods: {
    sendNewTodoThing() {
      this.isNewTodoIncluded = false;

      this.todoThings.forEach((item) => {
        if (
          item.todoThing.toLowerCase().trim() ===
          this.newTodoThing.toLowerCase().trim()
        ) {
          this.isNewTodoIncluded = true;
          this.errorOutput = "L' elemento è gia presente";
          this.$emit("notifyError", this.errorOutput);
          return;
        }
      });

      if (!this.isNewTodoIncluded && this.newTodoThing.length >= 3) {
        this.todoThings.unshift({
          todoThing: this.newTodoThing,
          isDone: false,
        });
        this.newTodoThing = "";
      } else if (!this.isNewTodoIncluded) {
        this.errorOutput = "Il numero minimo di caratteri è 3";
        this.$emit("notifyError", this.errorOutput);
      }
    },
  },
};
</script>

<template>
  <div class="input-container">
    <input
      v-model="newTodoThing"
      @keyup.enter="sendNewTodoThing"
      type="text"
      placeholder="Inserisci una cosa da fare"
    />
  </div>
</template>

<style lang="scss" scoped>
.input-container {
  position: sticky;
  top: 0;
  left: 0;
  height: 70px;
  width: 100%;
  background-color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  border-bottom: 2px dashed #85e89d;
  input {
    width: 85%;
    padding: 7px 17px;
    border-radius: 8px;
    border: 2px solid #85e89d;
    &:focus {
      outline: none;
      box-shadow: 0px 0px 10px gainsboro;
    }
    &::placeholder {
      text-align: center;
      color: #168031;
    }
  }
}
</style>
