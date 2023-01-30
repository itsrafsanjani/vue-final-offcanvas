# vue-final-offcanvas

A better Offcanvas for Vue.

Made with `Vue` and `TailwindCSS` goodness.

## Requirements

- [Vue 3](https://vuejs.org/)
- [TailwindCSS](https://tailwindcss.com/docs/guides/vite#vue)

For `Vue 2` Check [v2]('https://github.com/itsrafsanjani/vue-final-offcanvas/tree/v2') branch.

## Check Demo

Live: <https://vue-final-offcanvas-vue3-demo.netlify.app>

Source code: <https://github.com/itsrafsanjani/vue-final-offcanvas-vue3-demo>

## Installation

- Install the package

```shell
npm install vue-final-offcanvas
// OR
yarn add vue-final-offcanvas
```

- Update `tailwind.config.js`

```js
// tailwind.config.js

/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
    // add this line
    "./node_modules/vue-final-offcanvas/**/*.vue",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

```

## Usage

```vue
<template>
  <Offcanvas v-model="showOffcanvas">
    <template #header>
      <span>
        Hello World
      </span>
    </template>
    <section v-for="i in 20" :key="i">
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatum, itaque dolore! Aut non pariatur fugiat ad.
        Expedita distinctio nostrum minus ducimus temporibus non laudantium quae tempore similique nisi reiciendis
        doloremque neque molestiae quos itaque vel ipsum magni facere, rem, obcaecati, accusamus rerum repellat impedit
        nesciunt! Non magni consequatur unde a saepe. Assumenda maxime dolores animi modi beatae officia fugiat
        molestias provident amet veritatis earum accusamus recusandae repudiandae rem reprehenderit quia sit cumque a,
        adipisci laudantium! Quisquam, doloribus minima? Cupiditate pariatur asperiores amet error culpa magni, quam
        saepe fugit itaque modi. Odit voluptatum aspernatur esse alias quisquam dicta dolore incidunt inventore.
      </p>
      <hr class="my-3">
    </section>
  </Offcanvas>
  <button @click="toggleOffcanvas" class="px-5 py-3 bg-gray-200 hover:bg-gray-300 rounded">Toggle Offcanvas</button>
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
```

## License

[The MIT License](http://opensource.org/licenses/MIT)
