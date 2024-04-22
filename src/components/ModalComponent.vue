<template>
  <div class="main-container">
    <div :class="[theme === 'sale' ? 'sale-theme-modal' : 'normal-theme-modal']" class="modal-container">
      <div :class="[theme === 'sale' ? 'sale-theme-title' : 'normal-theme-title']" class="modal-title">{{ title }}</div>
      <div :class="[theme === 'sale' ? 'sale-theme-content' : 'normal-theme-content']" class="modal-content">{{ content }}</div>
      <div class="modal-links">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalComponent",
  props: {
    title: String,
    content: String,
    theme: String,
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
  border-radius: 10px;
  gap: 30px;
  /* background: #fff; */
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

.normal-theme-modal{
    background: #fff;
}

.sale-theme-modal{
    background: #EC283A;
}

.modal-title {
  font-size: 1.5rem;
  font-weight: 600;
}

.normal-theme-title{
    color: #05b7b0;
}

.sale-theme-content{
    color: #fff;
}

.normal-theme-content{
    color: #000;
}

.sale-theme-title{
    color:#fff
}

.modal-links{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
}
</style>
