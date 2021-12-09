<template>
  <div>
    Login

    <div class="form-group">
      <label for="username">Email : </label>
      <input v-model="user.email" type="text" name="email">
    </div>

    <div class="form-group">
      <label for="password">Password : </label>
      <input v-model="user.password" type="password" name="password">
    </div>

    <button @click="submitForm()">
      LETS GOOOO
    </button>
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
  name: 'WizmiLogin',
  layout: 'wizmi-base',
  props: { },

  setup () {
    const user = reactive(
      {
        email: '',
        password: ''
      }
    )
    const notifications = reactive({} as Notification)
    return {
      user,
      notifications
    }
  },

  methods: {
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
      if ((this.user.password === this.user.passwordVerify) && this.validateEmail()) {
        console.log(this.user)
      } else {
        console.log(this.notifications)
      }
    }
  }
}
</script>
