<template>
  <div class="login">
    <div class="login-left">
    </div>
    <div class="login-right">
      <form class="form">
        <div class="form-group">
          <label for="exampleInputEmail1">Email address</label>
          <input
            type="email"
            class="form-control"
            id="exampleInputEmail1"
            aria-describedby="emailHelp"
            placeholder="Enter email"
          />
          <small
            id="emailHelp"
            class="form-text text-muted"
          >We'll never share your email with anyone else.</small>
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Password</label>
          <input
            type="password"
            class="form-control"
            id="exampleInputPassword1"
            placeholder="Password"
          />
        </div>
        <div class="form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1" />
          <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.login {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100vh;
  background-color: var(--orange);
}
.login-right {
  display: flex;
  justify-content: center;
  background-color: #ffffff;
  width: 50vw;
  height: 80vh;
}
.form {
  align-items: center;
  width: 30vw;
  height: 50vh;
}
</style>
