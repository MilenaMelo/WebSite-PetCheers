<template>
  <div class="home">
    <div class="section-one"></div>
    <div class="section-two">
      <div class="image" @submit.prevent="submit()">
        <input
        ref="input"
        type="file"
        class="d-none"
        accept="image/*"
        @change="handleFile($event)"
        >
        <button
        type="button"
        class="btn"
        @click="openFile()">
        <i class="fa fa-camera"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    perfil: {
      file: ''
    }
  }),
  methods: {
    submit () {

    },
    handleFile ({ target }) {
      this.perfil.file = target.files[0]
    },
    openFile () {
      this.$refs.input.value = null
      this.$refs.input.click()
    }
  }
}
</script>

<style  lang="scss" scoped>
.home {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.section-one {
    height: 50vh;
    background-color: var(--orange);
  }
  .section-two {
     height: 50vh;
  }
</style>
