<template>
  <div id="app">
    <base-spinner/>
    <div class="container-fluid" v-if="isLogged">
      <div class="row">
        <div class="col-2 navigation-sidebar">
            <h1 class="container-fluid-title">PERFIL</h1>
            <layout-new-data></layout-new-data>
        </div>
        <div class="col">
             <router-view/>
        </div>
      </div>
    </div>
    <router-view v-else/>
  </div>
</template>

<script>
import BaseSpinner from './components/global/BaseSpinner'
import LayoutNewData from './components/layout/LayoutNewData'

export default {
  name: 'App',
  components: {
    BaseSpinner,
    LayoutNewData
  },
  data: () => ({ isLogged: false }),
  mounted () {
    this.$firebase.auth().onAuthStateChanged(user => {
      window.uid = user ? user.uid : null
      this.isLogged = !!user
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
.navigation-sidebar {
  background-color: var(--orange);
  .container-fluid-title {
    font-size: 18pt;
    margin-top: 10px;
    font-family: 'Poppins', 'Avenir', sans-serif;
  }
}
</style>
