<template>
  <div id="app">
    <base-spinner/>
    <router-view/>
  </div>
</template>

<script>
import BaseSpinner from './components/global/BaseSpinner'

export default {
  components: {
    BaseSpinner
  },
  mounted () {
    this.$firebase.auth().onAuthStateChanged(user => {
      window.uid = user ? user.uid : null
      this.$router.push({ name: window.uid ? 'home' : 'login' })
      this.$root.$emit('Spinner::hide')
    })
  }
}
</script>

<style lang="scss">
</style>
