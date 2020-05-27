<template>
  <i class="privacy-holder-icon iconfont" :class="`icon-${name}`" />
</template>

<script>
export default {
  name: "Icon",
  props: {
    name: {
      type: String,
      require: true
    }
  }
};
</script>

<style scoped lang="scss">
@import "./assets/iconfont.css";
.privacy-holder-icon {
  display: inline-block;
  font-size: 1.2em;
}
</style>
