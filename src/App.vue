<template>
  <div id="main__app">
    <forma @getProducts="toGetProducts" /> 
    <producti :products="products"/>
  </div>
</template>

<script>
import forma from '@/components/forma.vue'
import producti from '@/components/producti.vue'

export default {
  components: {
    forma,
    producti,
  },

  data() {
    return {
      products: []
    }
  },

  methods: {
    toGetProducts(data) {
      this.products = data
    }
  }
}

</script>

<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  overflow-x: hidden;
}

#app {
  padding: 20px 0;
}

#main__app {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

</style>
