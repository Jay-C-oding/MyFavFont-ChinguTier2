<template>
  <div>
    <nav class="nav">
      <input
        class="input1"
        type="search"
        placeholder="Search fonts"
        @keypress="searchQuery"
      />
      <input
        class="input2"
        type="text"
        v-model="updateText"
        :placeholder="[[inputText]]"
      />
      <div class="input3">
        <input
          id="pixel"
          type="number"
          placeholder="14"
          max="28"
          min="8"
          v-model="fontSize"
        />
        <span class="pixelText">px</span>
        <i class="fas fa-circle"></i>
        <i class="far fa-circle"></i>
      </div>
      <div id="extras">
        <i class="fas fa-list-ul"></i>
        <i class="fas fa-undo-alt"></i>
      </div>
    </nav>
    <section class="fontCards">
      <article id="eachFont" v-for="post in posts" :key="post">
        <link v-bind:href="myUrl" />
        <h3 class="fontName" :style="{ actualFont }">
          {{ post.family }}<i class="fas fa-plus-circle"></i>
        </h3>
        <h5 class="fontType">
          {{ post.category }}
        </h5>
        <p
          class="sampleText"
          :style="{ 'font-size': [[fontSize]] + 'px', actualFont }"
        >
          {{ updateText }}
        </p>
      </article>
    </section>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "fontInput",
  data() {
    return {
      posts: [],
      errors: [],
      searchQuery: "",
      noResult: "Sorry! Try different keyword?",
      inputText: "Check your font sample!",
      updateText: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
      fontSize: Number,
      sizeChange: "",
      fontName: [],
    };
  },
  methods: {
    fontFamily: function() {
      return this.posts.category;
    },
    myUrl: function() {
      return (
        "https://fonts.googleapis.com/css2?family=" +
        this.post.family +
        '&display=swap" rel="stylesheet'
      );
    },
    actualFont: function() {
      return "font-family: AbeeZee, sans-serif";
    },
  },

  created() {
    axios
      .get(
        `https://www.googleapis.com/webfonts/v1/webfonts?key=AIzaSyDaEHww-taTENK-JAPjSwwD9JeXKQdTblQ`
      )
      .then((response) => (this.posts = response.data.items))
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>

<style scoped>
.nav {
  border: 1px solid darkslategrey;
  border-radius: 20px;
  padding: 5px;
  color: darkslategrey;
  font-family: sans-serif;
  grid-area: nav;
  text-align: center;
  height: 3vh;
  display: flex;

  margin-top: 2vh;
  justify-content: space-around;
  align-items: center;
}
.input1 {
  outline: none;
  box-shadow: none;
  color: darkslategray;
  grid-area: input1;
  height: 1vw;
  width: 10vw;
  padding: 0.2rem;
  border: 0;
}
.input2 {
  grid-area: input2;
  outline: none;
  box-shadow: none;
  color: darkslategray;
  height: 1vw;
  width: 10vw;
  padding: 0.2rem;
  border: 0;
}
.input3 {
  grid-area: pixel;
  width: 10vw;
  height: 1vw;
  margin-bottom: 0.2rem;
}
#fontCards {
  margin-top: 1vw;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

#eachFont {
  width: 15vw;
  height: 15vw;
  display: inline-block;
  padding: 0.5rem;
  order: 4;
}

.fontName {
  position: relative;
  top: 0%;
  border-top: 1px solid darkslategrey;
  border-bottom: 1px solid darkslategrey;
  color: darkslategrey;
  margin-top: 0.5vw;
  margin-bottom: 1vw;
}
.fa-plus-circle {
  position: relative;
  left: 75%;
  font-size: 13px;
}
.fontType {
  margin-top: 0.5vw;
  text-align: right;
  color: darkslategrey;
  margin-bottom: 1.5vw;
}
.sampleText {
  color: darkslategrey;
  word-spacing: 5px;
  letter-spacing: 1px;
  margin-top: 1.5vw;
  margin-bottom: 2vw;
  display: inline-block;
}
</style>
