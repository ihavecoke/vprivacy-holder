<template>
  <div class="vprivacy-holder">
    <span v-if="showRawValue" class="raw-value">{{ rawValue }}</span>
    <span v-else class="privacy-value">{{ privacyValue }}</span>
    <slot name="privacyToggler">
      <icon
        :name="iconName"
        class="toggle-icon"
        @click.native="togglePrivacy"
      />
    </slot>
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
    // default hide raw value shown privacy value
    privacy: {
      type: Boolean,
      default: false
    },
    rawValue: {
      type: [String, Number],
      require: true
    },
    // predefined strategy like: phone, email, idCard...
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
    showRawValue() {
      return this.hiddenRawValue || !this.privacy;
    },
    privacyValue() {
      return Privacy[this.privacyStrategy](this.rawValue);
    },
    iconName() {
      return this.showRawValue ? "eye-open" : "eye-close";
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
