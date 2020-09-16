<template>
  <nav class="nav-bar">
      <ul class="nav flex-column">
        <li class="nav-item">
          <img class="img-fluid img-profile rounded-circle mx-auto mb-2" src="../../assets/images/ativo8.png" alt="">
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
  </nav>
</template>

<script>
export default {

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
  li {
    color: var(--featured);
  }
  .mb-2 {
    width: 8rem;
    height: 7rem;
    border: 0.5rem solid rgba(255, 255, 255, 0.2);
    background-color: var(--featured);
  }
}
</style>
