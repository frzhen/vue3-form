<template>
  <div class="container my-0 py-6">
    <VueButton />
    <VueInput />
    <SkillField />
  </div>
</template>

<script>
import VueButton from "@/components/VueButton.vue";
import VueInput from "@/components/VueInput.vue";
import SkillField from "@/components/SkillField.vue";

export default {
  name: "App",
  components: {
    VueButton,
    VueInput,
    SkillField,
  },
};
</script>

<style></style>
