<template>
  <div>
    <div class="block">
      <input
          class="is-primary mx-2"
          value="Hoodie"
          v-model="cloth"
          type="checkbox"
      >
      <label class="has-text-info">Hoodie</label>
      <input
          class="is-primary mx-2"
          value="Tee"
          v-model="cloth"
          type="checkbox"
      >
      <label class="has-text-info">Tee</label>
      <input
          class="is-primary mx-2"
          value="Fitted Cap"
          v-model="cloth"
          type="checkbox"
      >
      <label class="has-text-info">Fitted Cap</label>
      <input
          class="is-primary mx-2"
          value="Jacket"
          v-model="cloth"
          type="checkbox"
      >
      <label class="has-text-info">Jacket</label>
    </div>
    <div class="block pb-6">
      <p class="has-text-info">
        <span class="title is-4 has-text-primary">Your Favorite Fullstack clothing are:</span>
        <span v-for="item in cloth"
              :key="item"
              class="has-text-info mx-2">
        {{ item }}
      </span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ButtonRow",
  data() {
    return {
      cloth: []
    }
  }
};
</script>

<style lang="scss" scoped></style>
