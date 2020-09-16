<template>
  <div class="login">
    <div class="login-left">
    </div>
    <div class="login-right">
      <!-- The @submit.prevent="doLogin()" makes to active the function listened to get the informations in firebase -->
      <form @submit.prevent="doLogin()" class="form-login">
        <div class="form-group">
          <label for="exampleInputEmail1">E-mail</label>
          <input
            required
            type="email"
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
            class="form-control"
            id="exampleInputPassword1"
            placeholder="Senha"
          />
        </div>
        <!-- <div class="form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1" />
          <label class="form-check-label" for="exampleCheck1">Lembre de mim</label>
        </div> -->
        <button type="submit" class="btn btn-primary">Entrar</button>
      </form>
    </div>
  </div>
</template>

<script>
// Here the method is called for an action, passing the data like variables
export default {
  data: () => {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    doLogin () {
      console.log('feito')
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
.login-right {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffffff;
  width: 45vw;
  height: 90vh;
  border-radius: 10px;
}
.form-login {
  width: 30vw;
  height: 50vh;
}
</style>
