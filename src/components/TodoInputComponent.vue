<script>
export default {
  name: "TodoInputComponent",
};
</script>

<template>
  <div class="input-container">
    <input type="text" placeholder="Inserisci una cosa da fare" />
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
