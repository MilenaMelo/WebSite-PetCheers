<template>
  <div class="w-100 d-flex justify-content-center">
    <button class="btn btn-lg btn-primary">
      Inserir
    </button>
    <div class="modal fade" :class="{ show: showModal }" style="display: block">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLiveLabel">Modal title</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">×</span>
            </button>
          </div>
          <div class="modal-body">
            <p>Woohoo, you're reading this text in a modal!</p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary">Close</button>
            <button type="button" class="btn btn-primary">Save changes</button>
          </div>
        </div>
      </div>
    </div>
    <div class="modal-backdrop fade" :class="{ show: showModal }"></div>
  </div>
</template>

<script>
export default {
  data: () => ({ showModal: false })
}
</script>

<style lang="scss" scoped>
.btn-primary {
  background-image: none !important;
  background-color: var(--salmon) !important;
  font-size: 12pt;
   &:hover {
    background-color: var(--brown) !important;
  }
}
</style>
