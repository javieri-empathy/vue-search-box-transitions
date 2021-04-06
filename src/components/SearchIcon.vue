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
    <transition mode="out-in" name="search-loading-" :duration="500">
      <g v-if="isLoading" class="search-icon__spinner">
        <circle class="search-icon__spinner-bubble" cx="7" cy="11" r="0.25" />
        <circle class="search-icon__spinner-bubble" cx="11" cy="11" r="0.25" />
        <circle class="search-icon__spinner-bubble" cx="15" cy="11" r="0.25" />
      </g>
      <line
        v-else
        class="search-icon__handle"
        x1="21"
        x2="11"
        y1="21"
        y2="11"
      />
    </transition>
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

.search-icon {
  &__spinner {
    animation: rotate 1s ease-in-out infinite;
  }

  &__handle.search-loading {
    &--enter,
    &--leave-to {
      stroke-dashoffset: -14;
    }
    &--leave-active {
      transition: stroke-dashoffset 0.25s ease-in;
    }
    &--enter-active {
      transition: stroke-dashoffset 0.25s ease-out;
    }
  }

  &__spinner.search-loading {
    &--enter-active {
      .search-icon__spinner-bubble {
        transition: transform 0.25s var(--ease-out-back);
      }
    }

    &--leave-active {
      .search-icon__spinner-bubble {
        transition: transform 0.25s var(--ease-in-back);
      }
    }

    &--enter,
    &--leave-to {
      .search-icon__spinner-bubble {
        &:nth-child(1) {
          transform: translateX(4px);
        }
        &:nth-child(3) {
          transform: translateX(-4px);
        }
      }
    }
  }
}

@keyframes rotate {
  to {
    transform: rotateZ(360deg);
  }
}
</style>
