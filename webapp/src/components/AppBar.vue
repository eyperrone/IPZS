<template>
  <v-app-bar class="mt-10" elevation="0" style="background: none">
    <v-toolbar-title>
      <router-link to="/">
        <img src="../assets/logo.png" alt="" height="80" />
      </router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-title class="mr-8">
      <router-link to="/about"> About </router-link>
    </v-toolbar-title>
    <v-toolbar-title class="mr-8">
      <router-link to="/collections"> Collections </router-link>
    </v-toolbar-title>
    <v-toolbar-title v-if="logged" class="mr-8"> My NFTs </v-toolbar-title>
    <v-toolbar-title class="mr-8">
      <router-link to="/FAQs"> FAQs </router-link>
    </v-toolbar-title>
    <v-toolbar-title>
      <v-btn
        v-if="!logged && metamaskInstalled"
        color="#1A71CF"
        @click="login"
        dark
      >
        Connect wallet
      </v-btn>
      <v-btn v-if="logged && metamaskInstalled" color="#d7a8db" @click="logout">
        {{ walletAddress }}
      </v-btn>
      <v-btn v-if="!metamaskInstalled" color="#d7a8db" @click="install" dark>
        Install Metamask
      </v-btn>
    </v-toolbar-title>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      isMetamaskSupported: false,
      address: "",
      isLogged: false,
    };
  },
  computed: {
    logged() {
      // let logged = sessionStorage.getItem('logged')
      // if (logged && this.isLogged) {
      //     return true
      // } else {
      //     return false
      // }

      return this.isLogged;
    },
    metamaskInstalled() {
      if (typeof window.ethereum !== "undefined") {
        return true;
      } else {
        return false;
      }
    },
    walletAddress() {
      return this.address;
    },
  },
  mounted() {
    if (typeof window.ethereum !== "undefined") {
      console.log("Metamask is installed");
    }

    window.ethereum.on("accountsChanged", (accounts) => {
      console.log(accounts);
      this.address = accounts[0];
    });
  },
  methods: {
    async login() {
      sessionStorage.setItem("logged", true);
      const accounts = await window.ethereum.request({
        method: "eth_requestAccounts",
      });
      console.log(accounts);
      this.address = accounts[0];
      this.isLogged = true;
    },
    logout() {
      sessionStorage.clear();
      window.location.reload();
    },
    install() {
      window.open("https://metamask.io/", "_blank");
    },
  },
};
</script>
