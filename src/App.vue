<template>
  <div id="app">
    <div class="reveal">
      <div class="slides">
        <section><foo /></section> <!-- With vue-markdown-loader (loader config in vue.config.js)-->
        <section><div v-html="compiledMarkdown"></div></section> <!-- With marked js -->
        <section>
          <section>Vertical Slide 1</section>
          <section>Vertical Slide 2</section>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
import Reveal from 'reveal.js/js/reveal'
import Foo from "./components/foo.md"

let marked = require('marked');

export default {
  name: 'app',
  components: {
    Foo
  },

  data() {
    return {
      text: "# asd"
    }
  },

  computed: {
    compiledMarkdown: function () {
      return marked(this.text)
    }
  },

  mounted() {
    Reveal.initialize()
  }
}
</script>

<style>
@import url('../node_modules/reveal.js/css/reveal.css');
@import url('../node_modules/reveal.js/css/theme/white.css');

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
  height: 100vh;
}
</style>