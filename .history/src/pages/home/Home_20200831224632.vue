<template>
  <div class="home">
    <div class="section-one">
       <div class="section">
        <h1 class="display-2" >PET CHEERS</h1>
      </div>
      <div class="one-img">
        <img class="img" src="../../assets/images/img01.png" alt="">
      </div>
    </div>
    <div class="section-two">
      <!-- <div class="image" @submit.prevent="submit()">
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
        <div v-if="perfil.file">
          {{ perfil.file.name }}
          <button
          @click="perfil.file = ''"
          type="button"
          class="btn badge badge-light"
          >
          <i class="fa fa-trash text-danger"></i>
          </button>
        </div>
      </div> -->
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
  computed: {
    fileName () {
      const { receipt } = this.form
      if (receipt) {
        const split = receipt.name.split('.')
        return `${split[0]}-${new Date().getTime()}.${split[1]}`
      } else {
        return ''
      }
    }
  },
  methods: {
    async submit () {
      const ref = this.$firebase.database().ref(window.uid)
      const id = ref.push().key

      if (this.perfil.file) {
        // eslint-disable-next-line no-unused-vars
        const snapshot = await this.$firebase.storage()
          .ref(window.uid)
          .child()
      }
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
  height: 1000px;
}
.section-one {
    background-image: url('../../assets/images/ativo2.png');
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 600px;
    background-color: var(--orange);
    .img {
      height: 500px;
    }
    h1 {
      color: var(--featured);
    }
  }
  .section-two {
     height: 500px;
     background-color: var(--featured);
  }

</style>
