<template>
  <div id="app">
    <base-spinner/>
    <router-view/>
    <!-- <layout-new-data></layout-new-data> -->
  </div>
</template>

<script>
import BaseSpinner from './components/global/BaseSpinner'
// import LayoutNewData from './components/layout/LayoutNewData'

export default {
  components: {
    BaseSpinner
    // LayoutNewData
  },
  mounted () {
    this.$firebase.auth().onAuthStateChanged(user => {
      window.uid = user ? user.uid : null
      // eslint-disable-next-line no-undef
      console.log(uid)
      this.$router.push({ name: window.uid ? 'home' : 'login' }).catch(() => {})
      setTimeout(() => {
        this.$root.$emit('Spinner::hide')
      }, 1000)
    })
  }
}
</script>

<style lang="scss">
</style>
