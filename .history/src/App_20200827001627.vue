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
      // eslint-disable-next-line no-undef
      console.log(uid)
      this.$router.push({ name: window.uid ? 'home' : 'login' }).catch(() => {})
      this.$root.$emit('Spinner::hide')
      // setTimeout(() => {
      // }, 1000)
    })
  }
}
</script>

<style lang="scss">
</style>
