<template>
  <div
    class="w-full bg-white fixed top-0 right-0 xl:w-8/12 min-h-full z-50 shadow-xl transition ease-in-out delay-150 transform"
    :class="[visible ? 'translate-x-0' : 'translate-x-full']">
    <div
      class="relative z-10 bg-gray-100 shadow border-b py-5 px-4 flex w-full items-center dark:bg-gray-800 dark:border-gray-600 dark:text-white">
      <slot name="header"></slot>
      <div class="ml-auto flex">
        <button @click="toggle(false)" title="Close">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
            stroke="currentColor" class="h-9 w-9 text-red-500 hover:text-red-600">
            <path stroke-linecap="round" stroke-linejoin="round"
              d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
        </button>
      </div>
    </div>
    <div class="w-full px-6 offcanvas-body absolute top-16 pt-8 pb-16 dark:bg-gray-700">
      <slot v-if="visible"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "Offcanvas",

  data() {
    return {
      visible: false,
    };
  },

  props: {
    modelValue: {
      type: Boolean,
    },
  },

  watch: {
    modelValue(val) {
      setTimeout(() => this.toggle(val));
    },
  },

  methods: {
    clickOutside(e) {
      if (!this.$el.contains(e.target) && this.visible) {
        this.toggle(false);
      }
    },

    esc(e) {
      if (e.keyCode !== 27) return;

      this.toggle(false);
    },

    toggle(show) {
      if (show) {
        document.body.style.overflow = "hidden";
        this.visible = true;
      } else {
        this.$emit("update:modelValue", false);
        document.body.style.overflow = "auto";
        setTimeout(() => (this.visible = false), this.duration * 1000);
      }
    },
  },

  created() {
    setTimeout(() => document.addEventListener("click", this.clickOutside));

    setTimeout(() => document.addEventListener("keydown", this.esc));
  },

  beforeDestroy() {
    document.removeEventListener("click", this.clickOutside);

    document.removeEventListener("keydown", this.esc);
  },
};
</script>

<style scoped>
.offcanvas-body {
  height: calc(100vh - 2rem);
  overflow: auto;
}
</style>
