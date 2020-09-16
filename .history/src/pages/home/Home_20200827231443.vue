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
        <div v-if="perfil.name">
          {{ perfil.name }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    perfil: {
      name: '',
      file: ''
    }
  }),
  methods: {
    submit () {
      const ref = this.$firebase.database().ref(window.uid)
      const id = ref.push().key

      const payload = {
        id,
        file: null
      }
      ref.child(id).set(payload, err => {
        if (err) {
          console.log(err)
        } else {
          this.closeModal()
        }
      })
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
