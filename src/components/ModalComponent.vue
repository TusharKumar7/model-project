<template>
<div class="main-container">
  <div class="modal-container">
    <div class="modal-title">{{ title }}</div>
    <div class="modal-content">{{ content }}</div>
  </div>
</div>

</template>

<script>
export default {
  name: "ModalComponent",
  data() {
    return {};
  },
  props: {
    title: String,
    content: String,
  },
};
</script>

<style scoped>
.main-container {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  cursor: pointer;
  position: absolute;
  z-index: 1;
}

.modal-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 30px;
  background: #fff;
  border-radius: 10px;
  gap: 30px;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
  width: 25%;
  margin: 0 auto;
  position: absolute;
  inset: 0;
  top: 40%;
  height: max-content;
  z-index: 2;
  cursor: default;
}

.modal-title {
  color: #05b7b0;
  font-size: 1.5rem;
  font-weight: 600;
}

.modal-content {
  color: gray;
}
</style>
