<template>
  <div class="home">
        <section class="resume-section">
          <div class="resume-section">
            <img class="img d-lg-flex" src="../../assets/images/Ativo12.png" alt="">
             <div class="col-1 texts" >
                <p>Nome do PET: </p>
                <p>Idade do PET: </p>
             </div>
          </div>
        </section>
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
.resume-section{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}
.d-lg-flex {
  width: 40%;
}

</style>
