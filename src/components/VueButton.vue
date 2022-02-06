<template>
  <div class="block pt-6 mx-6 px-6">
    <div class="container">
      <div class="title is-4 has-text-primary">
        What is your favorite Fullstack clothing item?
      </div>
      <ButtonRow />
    </div>
  </div>
</template>

<script>
import ButtonRow from "@/components/ButtonRow.vue";
export default {
  name: "VueButton",
  components: {
    ButtonRow,
  },
};
</script>

<style lang="scss" scoped>
.block {
  background-color: white;
  border-radius: 5px;
}
</style>
