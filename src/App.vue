<template>
  <div class="app-container">
    <h1>My First Vue App</h1>
    <div class="input-container">
      <input type="text" ref="focusInput" />
    </div>
    <div class="btn-container">
      <button id="focus-btn" @click="focusInput()">Focus</button>
      <button id="modal-btn" @click="showModal()">Open Modal</button>
      <button id="theme-btn" @click="themeHandler()">
        {{ theme === "sale" ? "Normal Theme" : "Sale Theme" }}
      </button>
    </div>
  </div>
  <div class="modal" v-if="showModalComponent">
    <ModalComponent title="Sign up for the Giveaway!" content="Grab Your ninja swag for half price!" :theme="theme"
      @show-modal="showModal">
      <p :class="[theme === 'sale' && 'sale-content', 'content']">Hurray !!!</p>
      <template #links>
        <a href="#" :class="[btnThemeSelector, 'signup-button']">Sign Up</a>
        <a href="#" :class="[btnThemeSelector, 'login-button']">Login</a>
        <a href="#" :class="[btnThemeSelector, 'theme-btn']" @click="themeHandler()">
          {{ theme === 'sale' ? 'Normal Theme' : 'Sale Theme' }}
        </a>
      </template>
    </ModalComponent>
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
      showModalComponent: false,
      theme: "normal",
    };
  },
  methods: {
    focusInput() {
      setTimeout(() => {
        this.$refs.focusInput.focus();
      }, 1);
    },

    showModal() {
      this.showModalComponent = !this.showModalComponent;
    },

    themeHandler() {
      this.theme = this.theme === "sale" ? "normal" : "sale";
    },
  },
  computed: {
    btnThemeSelector() {
      return {
        'sale-theme-btn': this.theme === 'sale',
        'normal-theme-btn': this.theme !== 'sale',
      }
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

a {
  text-decoration: none;
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

.content {
  font-size: 1rem;
  margin: 0;
  padding: 0;
}

.sale-content {
  color: #fff;
}

.theme-btn {
  outline: none;
  border: none;
  padding: 7px 12px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
}

.signup-button,
.login-button {
  outline: none;
  padding: 7px 12px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
}

.normal-theme-btn {
  color: #05b7b0;
  background-color: #fff;
  border: 1px solid #05b7b0;
}

.sale-theme-btn {
  color: #ec283a;
  background-color: #fff;
  border: 1px solid #ec283a;
}

.btn-container button:hover {
  color: #2563eb;
  background-color: #fff;
  border: 1px solid #2563eb;
}
</style>
