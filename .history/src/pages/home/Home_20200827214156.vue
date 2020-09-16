<template>
  <div class="home">Home
    <div class="section-one"></div>
    <div class="section-two">
      <div class="image">
        <input
        ref="input"
        type="file"
        class="d-none"
        accept="image/*"
        >
        <button
        type="button"
        class="btn"
        @click="openFile()">
        <i class="fa fa-camera"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    openFile () {

    }
  }
}
</script>

<style>

</style>
