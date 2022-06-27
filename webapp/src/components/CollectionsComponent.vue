<template>
  <v-container class="container">
   <app-bar />
    <section class="pa-10" style="height: 85vh">
      <iframe
        src="https://opensea.io/assets/world-of-women-nft?embed=true"
        id="opensea-iframe"
        width="100%"
        height="100%"
        frameborder="0"
        allowfullscreen
      ></iframe>
    </section>
  </v-container>
</template>

<script>
import AppBar from './AppBar.vue'
export default {
  name: "CollectionsComponent",
  components: {
    'app-bar': AppBar
  },

  data: () => ({}),
};
</script>
