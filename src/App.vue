<template>
  <div id="app">
    <div class="demo">
      <div class="case">
        <h2>Phone Number</h2>
        <VPrivacyHolder raw-value="13800000000" privacy-strategy="mobile" />
      </div>
    </div>
  </div>
</template>

<script>
import VPrivacyHolder from "./components/VPrivacyHolder.vue";

export default {
  name: "App",
  components: {
    VPrivacyHolder
  }
};
</script>

<style type="scss" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 100px;
}
.case {
  text-align: left;
}
</style>
