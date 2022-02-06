<!--
  * @Author: Fred R. Zhen
  * @Date: 2022/2/7 01:16
  * @Email: fred.zhen@gmail.com
-->
<template>
  <div class="block my-3">
    <label>Skills: </label>
    <input
        class="input is-primary"
        type="text"
        v-model="tempSkill"
        @keyup="addSKill"
    >
  </div>
</template>

<script>
export default {
  name: "SkillField",
  data() {
    return {
      tempSkill: '',
      skills: []
    }
  },
  methods: {
    addSKill(event) {
      if (event.key === ',' && this.tempSkill) {
        this.skills.push(this.tempSkill);
        this.tempSkill = '';
      }
    }
  }
}
</script>

<style scoped>

</style>
