<template>
  <div class="container">
      <GraphViewVue></GraphViewVue>
  </div>
</template>

<script setup> 
import GraphViewVue from "./view/GraphView.vue";


</script>

<style  scoped>
.container{
  display: flex;
  justify-content: center;
  height: 100vh;
  background-color: antiquewhite;
  overflow: hidden;
}
body {
    font-family: 'DM Sans', sans-serif;
}

/* Para aplicar diferentes pesos de la fuente a elementos específicos */
h1 {
    font-weight: 700; /* Peso "Bold" */
}

p {
    font-weight: 400; /* Peso "Regular" */
}

</style>

