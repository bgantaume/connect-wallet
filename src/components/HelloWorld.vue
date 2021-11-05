<template>
  <div>
    <button v-on:click="test">Connect</button>
  </div>
</template>

<script>
// To interact with smart contracts
import { ethers } from "ethers";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  methods: {
    test: async function () {
      // for metamask (the plugin add "ethereum" to the window object)
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      console.log(provider);
      console.log(window.ethereum.selectedAddress);
      // request metamask to access the account
      await window.ethereum.request({ method: "eth_requestAccounts" });
      console.log(window.ethereum.selectedAddress);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
