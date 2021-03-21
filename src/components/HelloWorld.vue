<template>
  <div id="quote-box">
    <div id="text">{{ text }}</div>
    <div id="author">{{ author }}</div>
    <div id="new-quote">New Quote</div>
    <a href="twitter.com/intent/tweet" id="tweet-quote" target="_blank"></a>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";
export default defineComponent({
  name: "HelloWorld",
  setup: () => {
    const text = ref("");
    const author = ref("");
    return { text, author };
  },
});
</script>

<style scoped>
</style>
