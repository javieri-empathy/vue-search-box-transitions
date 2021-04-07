<template>
  <svg
    class="search-icon"
    fill="none"
    height="24"
    viewBox="0 0 24 24"
    width="24"
    xmlns="http://www.w3.org/2000/svg"
  >
    <circle cx="11" cy="11" r="8" />
    <g v-if="isLoading" class="search-icon__spinner">
      <circle class="search-icon__spinner-bubble" cx="7" cy="11" r="0.25" />
      <circle class="search-icon__spinner-bubble" cx="11" cy="11" r="0.25" />
      <circle class="search-icon__spinner-bubble" cx="15" cy="11" r="0.25" />
    </g>
    <line v-else class="search-icon__handle" x1="21" x2="11" y1="21" y2="11" />
  </svg>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "SearchIcon",
  props: {
    isLoading: {
      default: false,
      type: Boolean,
    },
  },
});
</script>

<style lang="scss" scoped>
.search-icon {
  stroke: currentColor;
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-width: 2;

  &__spinner,
  &__handle {
    transform-origin: 11px 11px;
  }

  &__handle {
    stroke-dasharray: 6.15 15;
  }
}
</style>
