<template>
  <div class="home">
        <section class="resume-section">
          <div class="resume-section">
            <img class="img d-lg-flex" src="../../assets/images/Ativo12.png" alt="">
            <div class="col">
              <div class="texts" >
                <p>Nome: {{ this.usuarios[0].description }} </p>
                <p>Idade: {{ this.usuarios[0].age }}  </p>
             </div>
            </div>
          </div>
        </section>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data: () => ({
    usuarios: []
  }),
  created () {
    this.getData()
  },
  computed: {
    // eslint-disable-next-line vue/return-in-computed-property
    getData () {
      const ref = this.$firebase.database().ref(`/${window.uid}`)
      ref.on('value', data => {
        const values = data.val()
        this.usuarios = Object.keys(values).map(i => values[i])
      })
    },
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
.col {
  margin-top: 100px;
}

</style>
