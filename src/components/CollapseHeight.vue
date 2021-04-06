<template>
  <transition
    v-on="$listeners"
    name="collapse-height-"
    @enter="expand"
    @leave="collapse"
    @after-enter="cleanUpAnimationStyles"
    @after-leave="cleanUpAnimationStyles"
  >
    <slot />
  </transition>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "CollapseHeight",
  inheritAttrs: false,
  methods: {
    expand(element: HTMLElement): void {
      element.style.height = "0";
      element.style.height = `${element.scrollHeight}px`;
    },
    cleanUpAnimationStyles(element: HTMLElement): void {
      element.style.removeProperty("height");
    },
    collapse(element: HTMLElement): void {
      element.style.height = `${element.scrollHeight}px`;
      element.getBoundingClientRect();
      element.style.height = "0";
    },
  },
});
</script>

<style lang="scss" scoped>
.collapse-height {
  &--enter-active {
    transition: height 0.35s var(--ease-out-back);
  }
  &--leave-active {
    transition: height 0.35s var(--ease-in-back);
  }
}
</style>
