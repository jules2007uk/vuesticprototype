<template>
  <div>
    <h1>AUTH TEST</h1>

    <!-- Check that the SDK client is not currently loading before accessing is methods -->
    <div v-if="!$auth.loading">
      <!-- show login when not authenticated -->
      <button v-if="!$auth.isAuthenticated" @click="login">Log in</button>
      <!-- show logout when authenticated -->
      <button v-if="$auth.isAuthenticated" @click="logout">Log out</button>

      <p v-if="$auth.isAuthenticated">Hi, {{ $auth.user.name }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'myvue1',
  methods: {
    // Log the user in
    login () {
      this.$auth.loginWithRedirect()
    },
    // Log the user out
    logout () {
      this.$auth.logout({
        returnTo: window.location.origin,
      })
    },
  },
  updated () {
    console.log(this.$auth)
  },
}
</script>
