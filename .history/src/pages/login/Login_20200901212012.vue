<template>
  <div class="login">
    <div class="login-left">
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
    </div>
    <div class="login-right">
      <!-- The @submit.prevent="doLogin()" makes to active the function listened to get the informations in firebase -->
      <form @submit.prevent="doLogin()" class="form-login">
        <div class="form-group">
          <label for="exampleInputEmail1">E-mail</label>
          <!-- The v-model directive will call the type 'email' and 'password'-->
          <input
            required
            type="email"
            v-model="email"
            class="form-control"
            id="exampleInputEmail1"
            aria-describedby="emailHelp"
            placeholder="Entrar com E-mail"
          />
          <small
            id="emailHelp"
            class="form-text text-muted"/>
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Senha</label>
          <input
            required
            type="password"
            v-model="password"
            class="form-control"
            id="exampleInputPassword1"
            placeholder="Senha"
          />
        </div>
        <!-- <div class="form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1" />
          <label class="form-check-label" for="exampleCheck1">Lembre de mim</label>
        </div> -->
        <button type="submit" class="btn btn-primary" :disabled = 'loading'>
          <template v-if="loading">
            <i class="fa fa-spinner fa-spin"></i>
          </template>
          <template v-else>
            Entrar
          </template>
        </button>
      </form>
    </div>
  </div>
</template>

<script>
// Here the method is called for an action, passing the data like variables
// And to pass the informations (variables) is necessary a directive: v-model as attribute
// of the input (HTML)
export default {
  name: 'Login',
  data: () => {
    return {
      loading: false,
      email: '',
      password: ''
    }
  },
  methods: {
    // Async method because has await the action of the auth()
    async doLogin () {
      this.loading = true
      // Use the firebase variable to authenticate by calling the auth(), authenticate method
      // signInWithEmailAndPassword() is a method
      // So, configure the authentication page in Firebase database and your
      const { email, password } = this

      try {
        const res = await this.$firebase.auth().signInWithEmailAndPassword(email, password)
        // variable window.uid to know if is logged
        window.uid = res.user.uid
        // redirect to Home page route
        this.$router.push({ name: 'home' })
      } catch (err) {
        console.log(err)
      }
      this.loading = false
    },
    beforeRouteEnter (to, from, next) {
      next(vm => {
        if (window.uid) {
          vm.$router.push({ name: 'home' })
        }
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.login {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100vh;
  background-color: var(--orange);
  padding-right: 50px;
  padding-left: 50px;
}
.login-right, .login-left {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--featured);
  width: 49%;
  height: 90%;
  border-radius: 10px;
}
.form-login {
  width: 30vw;
  height: 50vh;
}
.section-one {
    background-image: url('../../assets/images/ativo4.png');
    background-repeat: no-repeat;
    background-position: center;
    background-size: 40%;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    background-color: var(--featured);
    height: 100%;
    width: 100%;
    padding: 0px 70px 0px 90px;
    border-radius: 10px;
    .section-text {
      width: 130%;
      color: var(--brown);
      padding-bottom: 30px;
    }
    .img {
      width: 100%;
    }
}
@media (max-width: 10604px) {
  .login {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .login-left {
    display: none;
  }
}
</style>
