<template>
  <div class="home">
    <div class="section-one">
       <div class="section-text">
        <p class="display-5" >Pet Cheers is an
          application developed as a prototype of a
          mobile app to help with pet day activities.</p>
      </div>
      <div class="one-img">
        <img class="img" src="../../assets/images/img01.png" alt="">
      </div>
    </div>
    <div class="section-two">
      <button id="btnOn" type="button" class="btn btn-outline-secondary">Start</button>
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
  height: 100vh;
  background-color: var(--featured);
}
.section-one {
    background-image: url('../../assets/images/ativo4.png');
    background-repeat: no-repeat;
    background-position: center;
    background-size: auto;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    background-color: var(--featured);
    padding: 0px 70px 0px 120px;
    .section-text {
      width: 300px;
      color: var(--brown);
      padding-bottom: 30px;
    }
    .img {
      height: 500px;
    }
}
.section-two {
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
