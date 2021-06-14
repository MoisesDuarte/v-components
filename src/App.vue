<template>
  <div id="app">
    <form @submit.prevent="onSubmit">
      <AppInput
        id="username-input"
        label="Username:"
        type="text"
        v-model="loginData.username" 
      />

      <AppInput
        id="email-input"
        label="E-mail:"
        type="email"
        v-model="loginData.email" 
      />

      <AppInput
        id="password-input"
        label="Password:"
        type="password"
        hint="Min 8 characters"
        v-model="loginData.password" 
      />

      <AppSelect
        v-model="loginData.select"
        label="Company:"
        hint="Select your company"
        :options="options"
      />

      <AppTextArea
        v-model="loginData.description"
        id="textarea-input"
        label="Description:"
        hint="description goes here"
        :counter="true"
      />

      <AppCheckbox 
        v-model="loginData.remember"
        id="checkbox-input"
        label="Remember me"
      />

      <AppButton type="submit" color="primary">
        Submit
      </AppButton>

      <AppButton color="error" @click="clearForm">
        Clear Form
      </AppButton>
    </form>
  </div>
</template>

<script>
import AppInput from './components/AppInput';
import AppSelect from './components/AppSelect';
import AppTextArea from './components/AppTextArea';
import AppCheckbox from './components/AppCheckbox';
import AppButton from './components/AppButton';

export default {
  name: 'App',
  components: {
    AppInput,
    AppSelect,
    AppTextArea,
    AppCheckbox,
    AppButton,
  },
  data() {
    return {
      loginData: {
        username: null,
        email: null,
        password: null, 
        select: null,
        description: null,
        remember: true,
      },
      options: [
        'Ryura Incorporated',
        'Anathema Glasses',
        'Cunningham Accounting'
      ]
    }
  },
  methods: {
    onSubmit() {
      alert(JSON.stringify(this.loginData, null, 2));
    },
    clearForm() {
      this.loginData = {
        username: null,
        email: null,
        password: null, 
        select: null,
        description: null,
        remember: null,
      }
    }
  }
}
</script>

<style>
body {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 12px;
}
</style>
