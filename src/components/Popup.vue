<template>
  <transition-group name="popup-">
    <slot />
  </transition-group>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Popup",
  methods: {},
});
</script>

<style lang="scss"></style>
