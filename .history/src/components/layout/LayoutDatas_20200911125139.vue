<template>
<div>
  <button class="btn btn-lg btn-primary">
    Inserir
  </button>
  <div id="exampleModalLive" class="modal fade show">
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
          <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
          <button type="button" class="btn btn-primary">Save changes</button>
        </div>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {

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
