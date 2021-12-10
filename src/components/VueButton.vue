<template>
  <div class="block my-1 py-6 mx-6 px-6">
    <div class="container">
      <div class="title is-3 title-text">
        What is your favorite Fullstack clothing item?
      </div>
      <ButtonRow />
    </div>
  </div>
</template>

<script>
import ButtonRow from "./ButtonRow";
export default {
  name: "VueButton",
  components: {
    ButtonRow,
  },
};
</script>

<style lang="scss" scoped>
.block {
  background-color: #fdee88;
}
.title-text {
  color: #6668aa;
}
</style>
