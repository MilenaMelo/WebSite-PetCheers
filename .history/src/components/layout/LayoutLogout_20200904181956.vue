<template>
  <button class="btn btn.logout" @click="logout()">
    <i class="fa fa-power-off"></i>
    Sair
  </button>
</template>

<script>
export default {
methods: {
    async logout () {
      this.$root.$emit('Spinner::show')
      await this.$firebase.auth().signOut()
      this.$router.push({ name: 'login' })
      this.$root.$emit('Spinner::hide')
    }
}
}
</script>

<style lang="scss" scoped>
.btn {
  color: var(--featured) !important;
  &:hover {
    color: var(--brown) !important;
    translate: .4s;
  }
  &.active {
    color: var(--brown) !important;
  }
}
</style>
