<template>
  <v-app style="background-color: #1a71cf">
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    image: "@/assets/logo.png",
  }),
};
</script>
<style>
body,
html {
  height: 100% !important;
}

a {
  color: black !important;
  text-decoration: none !important;
}

.bg {
  /* The image used */
  /* background: #d7a8db !important; */
  background-image: url("/assets/background.jpg") !important;
  height: 100% !important;
  background-position: center !important;
  background-repeat: no-repeat !important;
  background-size: cover !important;
}

.container {
  min-height: 100vh;
  background: rgba(255, 255, 255, 1) !important;
  opacity: 1;
}

.container-spacer {
  padding-left: 10rem !important;
  padding-right: 10rem !important;
}

.title {
  font-size: 3rem !important;
}
</style>
