<template>
  <nav>
    <router-link
      :key="i"
      class="nav-bar"
      :to="{ name: router.name }"
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
  .mb-2 {
    width: 8rem;
    height: 7rem;
    border: 0.5rem solid rgba(255, 255, 255, 0.2);
    background-color: var(--featured);
  }
}
</style>
