<template>
<router-link
:key="i"
class="nav-bar"
:to="{ name: router.name }"
v-for="(router, i) in routerLinks"
>
  {{ router.meta.title }}
</router-link>
  <!-- <nav class="nav-bar">
      <ul class="nav flex-column">
        <li class="nav-item">
          <img class="img-fluid img-profile rounded-circle mx-auto mb-2" src="../../assets/images/img02.png" alt="">
        </li>
        <li class="nav-item">
          <a class="nav-link active" href="#">Active</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" href="#">Disabled</a>
        </li>
    </ul>
  </nav> -->
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
