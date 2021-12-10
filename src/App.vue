<template>
  <div class="container my-0 py-6">
    <VueButton />
    <VueInput />
  </div>
</template>

<script>
import VueButton from "./components/VueButton.vue";
import VueInput from "./components/VueInput";

export default {
  name: "App",
  components: {
    VueButton,
    VueInput,
  },
};
</script>

<style></style>
