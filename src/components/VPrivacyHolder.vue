<template>
  <div class="vprivacy-holder">
    <span v-if="showRawValue" class="raw-value">{{ rawValue }}</span>
    <span v-else class="privacy-value">{{ privacyValue }}</span>
    <div class="toggle-icon" v-if="showTrigger" @click="togglePrivacy">
      <slot name="privacyToggler">
        <icon :name="iconName" />
      </slot>
    </div>
  </div>
</template>

<script>
import Icon from "./icon/index.vue";
import Privacy from "privacy-holder";
export const ToggleEvent = "toggle";
export default {
  name: "VPrivacyHolder",
  components: { Icon },
  model: {
    prop: "privacy"
  },
  props: {
    // default hide raw value shown privacy value
    privacy: {
      type: Boolean,
      default: true
    },
    rawValue: {
      type: [String, Number],
      require: true
    },
    // predefined strategy like: phone, email, idCard...
    privacyStrategy: {
      type: String,
      default: "all"
    },
    showTrigger: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      showRawValue: false
    };
  },
  mounted() {
    this.showRawValue = !this.privacy;
  },
  computed: {
    privacyValue() {
      return Privacy[this.privacyStrategy](this.rawValue);
    },
    iconName() {
      return this.showRawValue ? "eye-close" : "eye-open";
    }
  },
  methods: {
    togglePrivacy() {
      this.showRawValue = !this.showRawValue;
      this.$emit(ToggleEvent, {
        privacy: this.showRawValue,
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
