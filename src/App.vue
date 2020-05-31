<template>
  <div id="app">
    <div class="demo">
      <div class="case">
        <h2>Phone Number</h2>
        <VPrivacyHolder raw-value="13800000000" privacy-strategy="mobile" />
      </div>
      <div class="case">
        <h2>Phone Number Default privacy</h2>
        <VPrivacyHolder
          raw-value="13800000000"
          privacy-strategy="mobile"
          :privacy="false"
        />
      </div>
      <div class="case">
        <h2>Phone Number No Toggle</h2>
        <VPrivacyHolder
          raw-value="13800000000"
          privacy-strategy="mobile"
          :show-trigger="false"
        />
      </div>
      <div class="case">
        <h2>Name</h2>
        <VPrivacyHolder raw-value="ihave coke" privacy-strategy="name" />
      </div>
      <div class="case">
        <h2>Email</h2>
        <VPrivacyHolder
          raw-value="ihavecoke@163.com"
          privacy-strategy="email"
        />
      </div>
      <div class="case">
        <h2>ID Card</h2>
        <VPrivacyHolder
          raw-value="51012416372290938"
          privacy-strategy="idCard"
        />
      </div>
      <div class="case">
        <h2>All Privacy</h2>
        <VPrivacyHolder raw-value="allStringsWillPrivacy" />
      </div>
      <div class="case">
        <h2>Custom Trigger</h2>
        <VPrivacyHolder raw-value="allStringsWillPrivacy">
          <template #privacyToggler>
            <a href="#" @click.stop.prevent>Shown</a>
          </template>
        </VPrivacyHolder>
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
  margin: 0 auto;
  max-width: 500px;
}
.case {
  text-align: left;
}
.case + .case {
  border-top: 1px solid #ccc;
  margin-top: 16px;
}
</style>
