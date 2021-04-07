<template>
  <transition-group
    name="popup-"
    v-bind="$attrs"
    v-on="$listeners"
    appear
    @afterEnter="removeDelay"
    @afterLeave="removeDelay"
    @beforeEnter="setDelay"
    @beforeLeave="setDelay"
  >
    <slot />
  </transition-group>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Popup",
  inheritAttrs: false,
  props: {
    staggerMs: {
      default: 30,
      type: Number,
    },
    baseDelayMs: {
      default: 0,
      type: Number,
    },
  },
  methods: {
    setDelay(element: HTMLElement) {
      const index = parseInt(element.dataset.index ?? "0");
      element.style.transitionDelay = `${
        this.baseDelayMs + this.staggerMs * index
      }ms`;
    },
    removeDelay(element: HTMLElement) {
      element.style.removeProperty("transitionDelay");
    },
  },
});
</script>

<style lang="scss">
.popup {
  &--enter-active {
    transition: 0.3s var(--ease-out-back);
    transition-property: opacity, transform;
  }

  &--leave-active {
    transition: 0.3s var(--ease-in-back);
    transition-property: opacity, transform;
  }

  &--enter,
  &--leave-to {
    opacity: 0;
    transform: scale(0.9);
  }
}
</style>
