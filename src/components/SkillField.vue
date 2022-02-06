<!--
  * @Author: Fred R. Zhen
  * @Date: 2022/2/7 01:16
  * @Email: fred.zhen@gmail.com
-->
<template>
  <div class="block my-3 has-background-white px-6 mx-6 py-6">
    <label class="title is-4 has-text-primary-dark">Skills: </label>
    <div class="field is-grouped is-grouped-multiline my-2">
      <div class="control"
           v-for="skill in skills"
           :key="skill">
        <div class="tags has-addons">
          <span class="tag is-info is-medium">
            {{ skill }}
          </span>
          <span class="tag is-delete is-medium" @click="removeSkill(skill)">

          </span>
        </div>
      </div>
    </div>
    <input
        class="input is-info mt-1"
        type="text"
        v-model="tempSkill"
        @keyup="addSkill"
        placeholder="Please Enter a new skill with comma or enter"
    >
<!-- TODO: try other tag addons-->
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
    addSkill(event) {
      // TODO: Catch double space
      if (event.key === ',' || event.key === 'Enter') {
        let skillString = this.tempSkill.trim();
        skillString = skillString.replace(',', '');
        if (skillString) {
          if (!this.skills.includes(skillString)) {
            this.skills.push(skillString);
          }
        }
        this.tempSkill = '';
      }
    },
    removeSkill(skillToRemove) {
      this.skills = this.skills.filter(skill => {
        return skill !== skillToRemove;
      });
    }
  }
}
</script>

<style scoped>

</style>
