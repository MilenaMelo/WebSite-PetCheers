<template>
  <div id="app">
    <base-spinner/>
    <div class="container-fluid" v-if="isLogged">
      <div class="row">
        <div class="col-2 navigation-sidebar">
            <layout-new-data></layout-new-data>
             <layout-data/>
        </div>
        <div class="col">
             <router-view/>
             <div class="texts" >
                <p>Nome do PET:  </p>
                <p>Idade do PET: </p>
             </div>
        </div>
      </div>
    </div>
    <router-view v-else/>
  </div>
</template>

<script>
import BaseSpinner from './components/global/BaseSpinner'
import LayoutNewData from './components/layout/LayoutNewData'
import LayoutData from './components/layout/LayoutData'

export default {
  name: 'App',
  components: {
    BaseSpinner,
    LayoutNewData,
    // eslint-disable-next-line vue/no-unused-components
    LayoutData
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
}
</style>
