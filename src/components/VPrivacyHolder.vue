<template>
  <div class="vprivacy-holder">
    <span v-if="hiddenRawValue" class="raw-value">{{ rawValue }}</span>
    <span v-else class="privacy-value">{{ privacyValue }}</span>
    <icon :name="iconName" class="toggle-icon" @click.native="togglePrivacy" />
  </div>
</template>

<script>
import Icon from "./icon";
const Privacy = require("privacy-holder");
export const ToggleEvent = "toggle";
export default {
  name: "VPrivacyHolder",
  components: { Icon },
  props: {
    rawValue: {
      type: [String, Number],
      require: true
    },
    privacyStrategy: {
      type: String,
      default: "all"
    }
  },
  data() {
    return {
      hiddenRawValue: false
    };
  },
  computed: {
    privacyValue() {
      return Privacy[this.privacyStrategy](this.rawValue);
    },
    iconName() {
      return this.hiddenRawValue ? "eye-open" : "eye-close";
    }
  },
  methods: {
    togglePrivacy() {
      this.hiddenRawValue = !this.hiddenRawValue;
      this.$emit(ToggleEvent, {
        privacy: this.hiddenRawValue,
        meta: this.rawValue
      });
    }
  }
};
</script>

<style scoped lang="scss">
.vprivacy-holder {
  display: flex;
  align-items: center;
  .toggle-icon {
    cursor: pointer;
    margin-left: 4px;
  }
}
</style>
