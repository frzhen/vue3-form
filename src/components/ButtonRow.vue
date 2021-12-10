<template>
  <div class="block">
    <button
      class="button is-primary mx-2"
      @click="onButtonClick"
      name="button-hoodie"
      value="fullstack-hoodie"
    >
      Hoodie
    </button>
    <button
      class="button is-primary mx-2"
      @click="onButtonClick"
      name="button-tee"
      value="fullstack-tee"
    >
      Tee
    </button>
    <button
      class="button is-primary mx-2"
      @click="onButtonClick"
      name="button-fitted-cap"
      value="fullstack-fitted-cap"
    >
      Fitted Cap
    </button>
    <button
      class="button is-primary mx-2"
      @click="onButtonClick"
      name="button-jacket"
      value="fullstack-jacket"
    >
      Jacket
    </button>
  </div>
</template>

<script>
export default {
  name: "ButtonRow",
  methods: {
    onButtonClick(event) {
      const buttonClicked = event.target;
      console.log(
        `The user clicked ${buttonClicked.name}: ${buttonClicked.value}`
      );
    },
  },
};
</script>

<style lang="scss" scoped></style>
