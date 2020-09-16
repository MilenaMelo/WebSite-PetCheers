<template>
  <div class="base-spinner" v-if="visible">
    <img src="../../assets/images/basespinner.png" alt="basespinner" />
    <ol class="items">
      <li class="circle-one" id="one"></li>
      <li class="circle-two" id="two"></li>
      <li class="circle-three" id="three"></li>
    </ol>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
var id = ['one', 'two', 'three']
// Defining the action of the base spinner

// eslint-disable-next-line eqeqeq
if (this.visible == true) {
  for (var x = 0; x < 10; x++) {
    setInterval(
      function () {
        document.getElementById('three').style.backgroundColor = '#FF8352'
      }, 250)
    setInterval(
      function () {
        document.getElementById('two').style.backgroundColor = '#FF8352'
      }, 500)
    setInterval(
      function () {
        document.getElementById('one').style.backgroundColor = '#FF8352'
      }, 1000)
    setInterval(
      function () {
        document.getElementById('three').style.backgroundColor = '#fff'
        document.getElementById('two').style.backgroundColor = '#fff'
        document.getElementById('one').style.backgroundColor = '#fff'
      }, 4000)
  }
}
// Component use
export default {
  // Variables
  data () {
    return {
      visible: true
    }
  },
  created () {
    // Event of the action (Spinner::show or Spinner::hide)
    // Listener of aplication
    this.$root.$on('Spinner::show', () => { this.visible = true })
    this.$root.$on('Spinner::hide', () => { this.visible = false })
  }
}

</script>

<style lang="scss" scoped>
@import '../../assets/scss/variables';

.base-spinner {
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  .items{
    list-style-type: none;
    padding-left: 3px;
    margin-bottom: 20x;
  }
  .circle-one, .circle-two, .circle-three {
    width: 35px;
    height: 35px;
    border-radius: 100%;
    margin-bottom: 4px;
  }
  .circle-two {
    margin-left: 10px;
  }
}
</style>
