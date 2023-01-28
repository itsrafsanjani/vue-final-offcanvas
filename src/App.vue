<template>
  <Offcanvas v-model="showOffcanvas">
    <template #header>
      <span>
        Hello World
      </span>
    </template>
    <div>
      <a href="https://vitejs.dev" target="_blank">
        <img src="/vite.svg" class="logo" alt="Vite logo" />
      </a>
      <a href="https://vuejs.org/" target="_blank">
        <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
      </a>
    </div>
  </Offcanvas>
  <button @click="toggleOffcanvas" class="hover:bg-gray-200">Toggle Offcanvas</button>
</template>

<script>
import Offcanvas from 'vue-final-offcanvas'
export default {
  components: {
    Offcanvas
  },

  data() {
    return {
      showOffcanvas: false
    }
  },

  methods: {
    toggleOffcanvas() {
      this.showOffcanvas = !this.showOffcanvas
    }
  }
}
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
