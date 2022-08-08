<template>
  <div class="container bg-dark">
    <Quote :writer="writers[localI]" :quoteTxt="texts[localI]" />

    <div class="btns mt-5 d-flex gap-2">
      <button class="btn btn-success" @click="localI = 0">to start</button>
      <button class="btn btn-success" :disabled="localI === writers.length-1" @click="localI++">next</button>
      <button class="btn btn-success" :disabled="localI == 0" @click="localI--">previuos</button>
      <button class="btn btn-success" @click="toEnd(writers)">to end</button>
    </div>
  </div>
</template>

<script>
import Quote from './components/Quote.vue';

export default {
  name: 'App',
  components: {
    Quote
  },
  data() {
    return {
      texts: [],
      writers: [],
      apiUrl: 'https://type.fit/api/quotes',
      index: 0,
      localI: localStorage.getItem('index')
    }
  },
  methods: {
    randomize(arr) {
      return Math.round( Math.random() * arr.length )
    },
    toEnd(arr) {
      this.localI = (arr.length -1)
      console.log(arr.length -1);
    }
  },
  mounted() {
    
    fetch(this.apiUrl)
    .then(response => response.json() )
    .then(response => {
      for (let i = 0; i < response.length; i++) {
        this.texts.push(response[i].text)
        this.writers.push(response[i].author)
      }
    })

    setInterval( () => {
      window.localStorage.setItem('index', this.localI);
    }, 100)
  },
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

body {
  background-color: rgb(46, 46, 46);
  overflow-x: hidden;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  width: 100%;
}

.container {
  background-color: rgb(46, 46, 46);
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}


</style>
