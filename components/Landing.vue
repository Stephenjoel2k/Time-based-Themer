<template>
  <div v-if="content" class="Home">
    <!-- Display if content is true -->
    <h2>Please Connect with spotify to continue!</h2>
    <!-- Placeholder until hosted -->
    <vs-button color="success" href="https://yourmusichabit.herokuapp.com/auth/login">
      <span>Spotify</span>
    </vs-button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      content: false
    }
  },
  mounted () {
    this.isValid()
    if (this.$route.query.accessToken !== undefined && this.$route.query.accessToken != null) {
      const accessToken = this.$route.query.accessToken
      localStorage.accessToken = accessToken
      const time = new Date()
      time.setMinutes(time.getMinutes() + 59)
      localStorage.expiry = time
      this.$router.push('dashboard')
    }
    this.content = true
  },
  methods: {
    isValid () {
      if (localStorage.expiry && localStorage.accessToken) {
        const time = new Date()
        const expiry = new Date(localStorage.expiry)
        localStorage.offset = time.getTimezoneOffset()
        if (expiry <= time) {
          localStorage.removeItem('accessToken')
          localStorage.removeItem('expiry')
          window.location.href = 'https://yourmusichabit.herokuapp.com/auth/login'
        } else {
          this.$router.push('/dashboard')
        }
      }
    }
  }
}
</script>
