<template>
  <div
    class="w-full bg-white fixed top-0 right-0 xl:w-8/12 min-h-full z-50 shadow-xl transition ease-in-out delay-150 transform"
    :class="[visible ? 'translate-x-0' : 'translate-x-full']">
    <div
      class="relative z-10 bg-gray-100 shadow border-b py-6 px-4 flex w-full items-center dark:bg-gray-800 dark:border-gray-600">
      <slot name="header"></slot>
      <div @click="toggle(false)"
        class="h-8 w-8 rounded-full shadow bg-white dark:bg-gray-900 text-xl inline-flex ml-auto justify-center align-center cursor-pointer border border-red-400 text-red-500">
        &times;
      </div>
    </div>
    <div class="px-6 offcanvas-body absolute top-16 pt-8 pb-16 dark:bg-gray-700">
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
