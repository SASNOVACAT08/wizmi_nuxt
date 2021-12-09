<template>
  <div>
    <h1>Register</h1>
    <form class="wizmi-form">
      <div class="wizmi-form-group">
        <label class="wizmi-label" for="username">Username</label>
        <input v-model="user.username" type="text" name="username" placeholder="Wizmi">
      </div>

      <div class="wizmi-form-group">
        <label class="wizmi-label" for="email">Email</label>
        <input v-model="user.email" type="text" name="email" placeholder="wizmi@gmail.com">
      </div>

      <div class="wizmi-form-group">
        <label class="wizmi-label" for="password">Password</label>
        <input v-model="user.password" type="password" name="password">
      </div>

      <div class="wizmi-form-group">
        <label class="wizmi-label" for="passwordVerify">Confirm password</label>
        <input v-model="user.passwordVerify" type="password" name="passwordVerify">
      </div>

      <button class="wizmi-button-primary" @click="submitForm()">
        LETS GOOOO
      </button>
    </form>
  </div>
</template>

<script lang="ts">
// TODO : CLEAN
enum NotificationTypes{
  Error = 'error'
}

interface Notification{
  type: NotificationTypes,
  message: string
}

export default {
  name: 'WizmiRegister',
  layout: 'wizmi-base',
  props: { },

  setup () {
    const user = reactive(
      {
        username: '',
        email: '',
        password: '',
        passwordVerify: ''
      }
    )
    const notifications = reactive({} as Notification)
    return {
      user,
      notifications
    }
  },

  methods: {
    validateUsername () {
      if (/^(?=.{4,20}$)(?![_.])(?!.*[_.]{2})[a-zA-Z0-9._]+(?<![_.])$/.test(this.user.username)) {
        return true
      } else {
        const notification: Notification = {
          type: NotificationTypes.Error,
          message: 'Please enter a valid username'
        }
        this.notifications.username = notification
        return false
      }
    },
    validateEmail () {
      if (/^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(this.user.email)) {
        return true
      } else {
        const notification: Notification = {
          type: NotificationTypes.Error,
          message: 'Please enter a valid email address'
        }
        this.notifications.email = notification
        return false
      }
    },
    submitForm () {
      if ((this.user.password === this.user.passwordVerify) && this.validateUsername() && this.validateEmail()) {
        console.log(this.user)
      } else {
        console.log(this.notifications)
      }
    }
  }
}

</script>
