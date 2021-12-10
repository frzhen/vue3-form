<template>
  <div class="block mx-6 px-6 py-6 my-1">
    <div class="title is-3 input-title">Fullstack Clothing Inquiry Sheet</div>
    <div class="columns">
      <div class="column">
        <form action="" class="form" @submit.prevent="submitForm">
          <!--  User Name Field -->
          <div id="userName" class="field mx-6 my-4 has-text-primary">
            <div class="control has-icons-left has-icons-right">
              <input
                id="item"
                class="input is-primary"
                v-model="fields.userName"
                type="text"
                placeholder="username"
              />
              <span class="icon is-left has-text-info">
                <em class="fas fa-user"></em>
              </span>
              <span v-if="isValidUserName" class="icon is-right has-text-success">
                <em class="fas fa-check"></em>
              </span>
              <span v-if="!isValidUserName" class="icon is-right has-text-grey-lighter">
                <em class="fas fa-check"></em>
              </span>
              <span class="has-text-danger">{{ fieldsErrors.userName }}</span>
            </div>
          </div>
          <!--  Email Field -->
          <div id="email" class="field mx-6 my-4">
            <div class="control has-icons-left has-icons-right">
              <input
                v-model="fields.email"
                class="input is-primary"
                placeholder="Email"
                type="email"
              />
              <span class="icon is-left has-text-primary">
                <em class="fas fa-envelope"></em>
              </span>
              <span v-if="isValidEmail" class="icon is-right has-text-success">
                <em class="fas fa-check"></em>
              </span>
              <span v-if="!isValidEmail" class="icon is-right has-text-grey-lighter">
                <em class="fas fa-check"></em>
              </span>
              <span class="has-text-danger">{{ fieldsErrors.email }}</span>
            </div>
          </div>
          <!--  Password Field -->
          <div id="password" class="field mx-6 my-4">
            <div class="control has-icons-left has-icons-right">
              <input
                v-model="fields.password"
                class="input is-primary"
                placeholder="Password"
                type="password"
              />
              <span class="icon is-left has-text-primary">
                <em class="fas fa-key"></em>
              </span>
              <span v-if="isValidPassword" class="icon is-right has-text-success">
                <em class="fas fa-check"></em>
              </span>
              <span v-if="!isValidPassword" class="icon is-right has-text-grey-lighter">
                <em class="fas fa-check"></em>
              </span>
              <span class="has-text-danger">{{ fieldsErrors.password }}</span>
            </div>
          </div>
          <!--  Priority/Urgency Field -->
          <div id="priority" class="field my-2 ml-6">
            <div class="control has-icons-left">
              <div class="select is-info">
                <select class="has-text-grey has-background-white"
                        v-model="fields.priority">
                  <option value="" disabled>Select Priority</option>
                  <option value="Nonessential">Nonessential</option>
                  <option value="Moderate">Moderate</option>
                  <option value="Urgent">Urgent</option>
                </select>
              </div>
              <span class="icon is-left has-text-info">
                <em class="fas fa-exclamation-triangle"></em>
              </span>
              <span class="has-text-danger" v-if="isNotUrgent">
                Must be moderate or urgent
              </span>
              <div class="has-text-danger">{{ fieldsErrors.priority }}</div>
            </div>
          </div>
          <!--  Terms and Conditions Field -->
          <div id="terms" class="field mx-6 my-4">
            <div class="control">
              <label class="checkbox">
                <input
                  v-model="fields.termsAndConditions"
                  type="checkbox"
                  class="is-info mr-2"
                />
                I accept the
                <a href="https://www.1dataops.com" class="has-text-success">
                  terms and conditions
                </a>
              </label>
              <div class="has-text-danger">
                {{ fieldsErrors.termsAndConditions }}
              </div>
            </div>
          </div>
          <!--  Buttons Field -->
          <div
            id="buttons"
            class="field is-grouped is-justify-content-flex-end mt-2 mx-6">
            <div class="control">
              <button class="button is-link" :disabled="disabled">
                Submit
              </button>
            </div>
            <div class="control">
              <button class="button is-link is-light">Cancel</button>
            </div>
          </div>
        </form>
      </div>
      <div class="column is-one-third-tablet is-half-widescreen"></div>
    </div>
    <div class="message">
      <div class="message-content px-6">
        <ul>
          <li v-for="item in itemList" :key="item">
            {{ item }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VueInput",
  data() {
    return {
      fields: {
        userName: "",
        email: "",
        password: "",
        priority: "",
        termsAndConditions: false,
      },
      fieldsErrors: {
        userName: undefined,
        email: undefined,
        password: undefined,
        priority: undefined,
        termsAndConditions: undefined,
      },
      itemList: [],
      loading: false,
      saveStatus: "READY",
    };
  },
  computed: {
    isValidUserName() {
      const re = /^[A-Za-z0-9_-]{3,20}$/;
      return re.test(this.fields.userName);
    },
    isValidEmail() {
      const re = /\S+@\S+\.\S+/;
      return re.test(this.fields.email);
      },
    isValidPassword() {
      const re = /(?=(.*\d))((?=.*[A-Za-z0-9])(?=.*[A-Z])(?=.*[a-z]))^.{8,}$/;
      return re.test(this.fields.password);
    },
    isNotUrgent() {
      return (this.fields.priority === "Nonessential" || this.fields.priority === undefined);
    },
    disabled() {
      if (!this.isNotUrgent && this.isValidUserName && this.isValidEmail && this.isValidPassword) {
        return 0;
      } else {
        return 1;
      }
    }
  },
  methods: {
    resetFields() {
      this.fields.userName = "";
      this.fields.email = "";
      this.fields.password = "";
      this.fields.priority = "";
      this.fields.termsAndConditions = false;
    },
    submitForm() {
      this.fieldsErrors = this.validateForm(this.fields);
      if (Object.keys(this.fieldsErrors).length) return;

      this.itemList.push(this.fields.userName);
      this.resetFields();
    },
    validateForm(fields) {
      const errors = {};
      if (!fields.userName) errors.userName = "The username is required";
      if (!fields.email) errors.email = "The email is required";
      if (!fields.password) errors.password = "The password is required";
      if (!fields.priority) errors.priority = "The priority needs be selected";
      if (!fields.termsAndConditions) {
        errors.termsAndConditions = "The Terms and Conditions need be approved";
      }
      if (fields.email && !this.isValidEmail()) {
        errors.email = "Invalid Email";
      }
      if (fields.password && !this.isValidPassword()) {
        errors.password = "Not Valid Password";
      }
      return errors;
    },


  },
};
</script>

<style lang="scss" scoped>
.block {
  background-color: #fdee88;
}
.input-title {
  color: #6668aa;
}
div.message {
  background-color: #fdee88;
  color: #6668aa;
}
</style>
