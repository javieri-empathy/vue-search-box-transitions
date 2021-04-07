<template>
  <button :class="cssClasses" class="suggestion">
    <span class="suggestion__category">{{ item.category }}</span>
    <span class="suggestion__label">{{ item.query }}</span>
    <ChevronIcon class="suggestion__icon" />
  </button>
</template>

<script lang="ts">
import ChevronIcon from "@/components/ChevronIcon.vue";
import { QuerySuggestion } from "@/models/suggestion.model";
import Vue, { PropType } from "vue";

export default Vue.extend({
  name: "Suggestion",
  components: { ChevronIcon },
  props: {
    item: {
      required: true,
      type: Object as PropType<QuerySuggestion>,
    },
  },
  computed: {
    cssClasses(): string[] {
      return [`suggestion--in-${this.item.category}`];
    },
  },
});
</script>

<style lang="scss" scoped>
.suggestion {
  display: flex;
  align-items: center;
  padding: 0.5em;
  cursor: pointer;
  text-align: left;
  border-radius: 8px;
  background: none;

  &__category {
    font-size: var(--font-size-small);
    font-weight: bold;
    display: block;
    padding: 0.25em 0.35em;
    text-transform: uppercase;
    color: var(--white-color);
    border-radius: 4px;
  }

  &__label {
    font-size: var(--font-size-big);
    margin-left: 0.5em;
  }

  &__icon {
    margin-left: auto;
    color: var(--light-font-color);
  }

  &--in-looks {
    .suggestion__category {
      background-color: #0096f5;
    }
  }

  &--in-men,
  &--in-women {
    .suggestion__category {
      background-color: #333645;
    }
  }
}

.suggestion {
  transition: background-color 0.2s ease-out;

  &:hover {
    background: var(--light-highlight-color);
  }
}
</style>
