<template>
  <div id="quote-box">
    <div id="text">{{ text }}</div>
    <div id="author">- {{ author }}</div>
    <div id="options">
      <a
        :href="`https://twitter.com/intent/tweet?hashtags=quotes&related=freecodecamp&text=\&quot;${text}\&quot; ${author}`"
        id="tweet-quote"
        target="_blank"
      >
        Tweet Quote
      </a>
      <div id="new-quote" @click="newQupte">New Quote</div>
    </div>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";
import data from "../data.json";
export default defineComponent({
  name: "HelloWorld",
  setup: () => {
    let text = ref("");
    let author = ref("");
    const getRandomInt = (max: number) => {
      return Math.floor(Math.random() * Math.floor(max));
    };
    let oldRandomNum: number;
    const newQupte = () => {
      let randomNum = getRandomInt(data.length);
      if (oldRandomNum === randomNum) {
        newQupte();
        return;
      }
      oldRandomNum = randomNum;
      text.value = data[randomNum].text;
      author.value = data[randomNum].author;
    };
    newQupte();
    return { text, author, newQupte };
  },
});
</script>
<style lang="scss" scoped>
#quote-box {
  width: 600px;
  display: grid;
  grid-template-rows: auto auto auto;
  background: #def;
  padding: 30px 40px;
}
#text {
  font-size: 30px;
  transition-duration: 0.3s;
  padding-bottom: 10px;
}
#author {
  font-size: 20px;
  justify-self: end;
  transition-duration: 0.3s;
  padding-bottom: 20px;
}
#options {
  display: flex;
  justify-content: space-between;
  align-items: center;
  #new-quote {
    cursor: pointer;
    background: #abc;
    padding: 5px 10px;
    transition-duration: 0.3s;
    &:hover {
      background: #789;
    }
  }
  #tweet-quote {
    background: #abc;
    padding: 5px 10px;
    transition-duration: 0.3s;
    text-decoration: none;
    color: #000;
    &:hover {
      background: #789;
    }
  }
}
</style>