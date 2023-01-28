# vue-final-offcanvas

A better Offcanvas for Vue.

No special dependencies, no jquery, no bootstrap, just VueJS and CSS goodness.

## Requirements

- [Vue.js](https://github.com/vuejs/vue)

## Installation

```shell
$ npm install vue-final-offcanvas
// OR
$ yarn add vue-final-offcanvas
```

## Usage

```vue
<template>
  <button @click="toggleOffcanvas" class="button-primary">Toggle Offcanvas</button>

  <Offcanvas v-model="showOffcanvas">
    <div slot="header">
      <h1 class="dark:text-white">Hello World</h1>
    </div>
    <section v-for="i in 20" class="bg-gray-50" :key="i">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. A ad culpa delectus dolorem ea eligendi error!
      </p>
    </section>
  </Offcanvas>
</template>

<script>
export default {
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
```

## License

[The MIT License](http://opensource.org/licenses/MIT)
