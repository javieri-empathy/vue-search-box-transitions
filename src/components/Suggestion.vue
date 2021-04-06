<template>
  <button class="suggestion">
    <span class="suggestion__label">{{ query }}</span>
    <ChevronIcon class="suggestion__icon" />
  </button>
</template>

<script lang="ts">
import ChevronIcon from "@/components/ChevronIcon.vue";
import Vue from "vue";

export default Vue.extend({
  name: "Suggestion",
  components: { ChevronIcon },
  props: {
    query: {
      required: true,
      type: String,
    },
  },
});
</script>

<style lang="scss" scoped>
.suggestion {
  display: flex;
  align-content: center;
  justify-content: space-between;
  padding: 0.5em;
  cursor: pointer;
  text-align: left;
  border-radius: 8px;
  background: none;

  &__icon {
    color: var(--light-font-color);
  }

  &__label {
    font-size: var(--font-size-big);
  }
}

.suggestion {
  transition: background-color 0.2s ease-out;

  &:hover {
    background: var(--light-highlight-color);
  }
}
</style>
