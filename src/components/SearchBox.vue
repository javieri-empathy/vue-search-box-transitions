<template>
  <div class="search-box">
    <div class="search-box__input-wrapper">
      <SearchIcon :is-loading="isLoading" class="search-box__icon" />
      <input
        class="search-box__input"
        @blur="hasFocus = false"
        @focus="hasFocus = true"
        @input="fakeSearch"
      />
    </div>
    <section v-if="hasFocus" class="search-box__suggestions-wrapper">
      <h2 class="search-box__suggestions-title">Trending searches</h2>
      <ul class="search-box__suggestions-list">
        <li
          v-for="suggestion in recentSearches"
          :key="suggestion.query"
          class="search-box__suggestion-item"
        >
          <Suggestion :item="suggestion" class="search-box__suggestion" />
        </li>
      </ul>
    </section>
  </div>
</template>

<script lang="ts">
import SearchIcon from "@/components/SearchIcon.vue";
import Suggestion from "@/components/Suggestion.vue";
import { QuerySuggestion } from "@/models/suggestion.model";
import Vue from "vue";

interface SearchBoxData {
  fakeSearchId: number | null;
  hasFocus: boolean;
  isLoading: boolean;
  recentSearches: QuerySuggestion[];
}

export default Vue.extend({
  name: "SearchBox",
  components: { Suggestion, SearchIcon },
  data(): SearchBoxData {
    return {
      isLoading: false,
      hasFocus: false,
      fakeSearchId: null as number | null,
      recentSearches: [
        { category: "looks", query: "Spring styles" },
        { category: "men", query: "Shirt" },
        { category: "women", query: "Dress" },
        { category: "women", query: "Jeans" },
        { category: "men", query: "Jacket" },
      ],
    };
  },
  computed: {},
  methods: {
    fakeSearch(): void {
      this.isLoading = true;
      if (this.fakeSearchId !== null) {
        clearTimeout(this.fakeSearchId);
      }
      this.fakeSearchId = setTimeout(() => {
        this.isLoading = false;
      }, 1500);
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
$input-height: 3em;

.search-box {
  font-size: var(--font-size-very-big);
  overflow: hidden;
  border: solid 2px var(--background-color);
  border-radius: 13px;
  background: var(--white-color);
  box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.15);

  &__input-wrapper {
    position: relative;
  }

  &__icon {
    position: absolute;
    top: 1em;
    left: 1em;
    color: var(--light-font-color);
  }

  &__input {
    line-height: $input-height;
    width: 100%;
    height: $input-height;
    padding: 0 0 0 $input-height;
    color: var(--font-color);
    border: none;
    background: none;
  }

  &__suggestions-wrapper {
    padding: 0 1em;
    border-top: solid 1px var(--background-color);
  }

  &__suggestions-title {
    font-size: var(--font-size-big);
    margin: 2em 0 0 0;
    color: var(--light-font-color);
  }

  &__suggestions-list {
    padding: 0.25em 0;
    list-style: none;
  }

  &__suggestion-item {
    margin: 0.25em -0.5em;
  }

  &__suggestion {
    width: 100%;
    height: 100%;
  }
}
</style>
