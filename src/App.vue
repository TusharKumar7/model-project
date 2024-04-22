<template>
  <div class="app-container">
    <h1>My First Vue App</h1>
    <div class="input-container">
      <input type="text" ref="focusInput" />
    </div>
    <div class="btn-container">
      <button id="focus-btn" @click="focusInput()">Focus</button>
      <button id="modal-btn" @click="showModal = true">Open Modal</button>
    </div>
  </div>
  <div class="modal" v-if="showModal" @click="closeModal()">
    <ModalComponent
      title="Sign up for the Giveaway!"
      content="Grab Your ninja swag for half price!"
    />
  </div>
</template>

<script>
import ModalComponent from "./components/ModalComponent.vue";

export default {
  name: "App",
  components: {
    ModalComponent,
  },
  data: function () {
    return {
      showModal: false,
    };
  },
  methods: {
    focusInput() {
      setTimeout(() => {
        this.$refs.focusInput.focus();
      }, 1);
    },
    closeModal() {
      this.showModal = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
  position: relative;
}

.btn-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
}

.input-container input {
  border: 1px solid #64748b;
  border-radius: 3px;
  font-size: 1rem;
  padding: 3px 6px;
}

.btn-container button {
  color: white;
  background-color: #2563eb;
  outline: none;
  border: none;
  padding: 7px 12px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
}

.btn-container button:hover {
  color: #2563eb;
  background-color: #fff;
  border: 1px solid #2563eb;
}
</style>
