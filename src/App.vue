<template>
  <div id="app">
    <SearchBox class="app-search-box" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import SearchBox from "./components/SearchBox.vue";

export default Vue.extend({
  name: "App",
  components: {
    SearchBox,
  },
});
</script>

<style lang="scss">
:root {
  --background-color: #e4e6ed;
  --light-highlight-color: #eaecf0;
  --font-color: #333645;
  --light-font-color: #b6b9c5;
  --white-color: #f6f8fa;

  --font-size-standard: 16px;
  --font-size-big: 20px;
  --font-size-very-big: 24px;

  --ease-out-back: cubic-bezier(0.175, 0.885, 0.32, 1.275);
  --ease-in-back: cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

body {
  background: var(--background-color);
}

body,
html {
  height: 100%;
  margin: 0;
  padding: 0;

  * {
    margin: 0;
    padding: 0;
    border: none;
    outline: none;
    box-sizing: border-box;
    font-size: inherit;
  }
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  width: 100%;
  height: 100%;
  color: var(--font-color);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.app-search-box {
  width: 100%;
  max-width: 40em;
  margin: 20em 0 0 0;
}
</style>
