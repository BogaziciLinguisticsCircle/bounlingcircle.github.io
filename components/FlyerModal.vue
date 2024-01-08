<template>
  <div class="modal-overlay" @click="$emit('close-modal')">
    <div class="modal" @click.stop>
      <img src="~/assets/SCOL24Flyer.png" alt="conference flyer with a picture of albert long hall at bogazici university" style="max-height: 100%; width: auto"/>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>

.modal-overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  background-color: #000000da;
}

.modal {
  text-align: center;
  background-color: white;
  max-height: 100%;
  width: auto%;
  margin: 2%;
  border-radius: 20px;
}
.close {
  margin: 10% 0 0 16px;
  cursor: pointer;
}
</style>