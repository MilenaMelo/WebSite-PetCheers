<template>
  <nav class="nav-bar flex-column">
    <ul class="nav flex-column">
      <li class="nav-item">
        <img class="img-fluid img-profile rounded-circle mx-auto mb-2" src="../../assets/images/img2.jpg" alt="">
      </li>
   </ul>
    <router-link
      :key="i"
      exact
      class="routerlinks"
      :to="{ name: router.name }"
      exact-active-class="active"
      v-for="(router, i) in routerLinks"
      >
      {{ router.meta.title }}
    </router-link>
  </nav>
</template>

<script>
export default {
  computed: {
    routerLinks () {
      return this.$router.options.routes.filter(r => r.name !== 'login')
    }
  }
}
</script>

<style lang="scss" scoped>
.nav-bar {
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  ul {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .nav-item {
        margin-bottom: 20px;
  }
  .mb-2 {
    width: 8rem;
    height: 8rem;
    border: 0.2rem solid rgba(255, 255, 255, 0.2);
    background-color: var(--featured);
    margin-bottom: 30px;
  }
}
</style>
