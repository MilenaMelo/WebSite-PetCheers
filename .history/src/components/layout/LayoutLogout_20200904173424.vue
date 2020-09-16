<template>
  <button class="btn btn-primary">
    <i class="fa fa-power-off"></i>
    Sair
  </button>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.btn.logout {
  width: 200px;
  color: var(--orange) !important;
  border-color: var(--orange) !important;
  &:hover, &:visited, &:active {
    background-color:  var(--orange) !important;
    color: var(--featured) !important;
  }
}
a {
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
