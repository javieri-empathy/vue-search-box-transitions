<template>
  <transition name="collapse-height-">
    <slot />
  </transition>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "CollapseHeight",
  methods: {},
});
</script>

<style lang="scss" scoped></style>
