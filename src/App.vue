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
