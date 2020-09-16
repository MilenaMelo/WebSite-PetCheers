<template>
  <div class="login">
    <div class="login-left">

    </div>
    <div class="login-right">
       <form class="form-login">
        <div class="card">
          <div class="card-header text-center">
            <h1 class="mb-0">Expenses</h1>
          </div>
          <div class="card-body">
            <div class="form-group">
              <input
                required
                type="email"
                v-model="email"
                class="form-control"
                placeholder="E-mail"
              >
            </div>
            <div class="form-group">
              <input
                required
                type="password"
                v-model="password"
                class="form-control"
                placeholder="Senha"
              >
            </div>
            <button class="btn btn-primary w-100" >
              <template >
                Entrando...
                <i class="fa fa-spinner fa-spin"></i>
              </template>
              <template>
                Entrar
                <i class="fa fa-sign-in-alt"></i>
              </template>
            </button>
          </div>
        </div>
    </form>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
