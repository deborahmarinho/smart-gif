<template>
  <div class="GifHome">
    <h1>{{ msg }}</h1>
    <p style="white-space: pre-line;">{{ text }}</p>
    <textarea v-model="text" placeholder="Digite uma frase para encontrar um gif"></textarea>
    <iframe v-if="text != null" :src="gifUrlProperty" crossorigin="anonymous"/>
  </div>
</template>

<script>
import axios from "axios"
export default {
  data() {
    return {
      text: null,
      gifUrl: null,
    };
  },
  name: 'GifHome',
  props: {
    msg: String
  },
  computed: {
    gifUrlProperty: function() {
      (async () => await this.fetch(this.text))();
        return this.gifUrl;
      }
  },
  methods: {
    async fetch(text) {
        var response = await axios
          .get("https://api.giphy.com/v1/gifs/search?api_key=Y6UQI9PdJql4SJuWHaBwjkCmLnVblxsa&q=" + text + "&limit=1&offset=0&rating=g&lang=en&bundle=messaging_non_clips")
            this.gifUrl = response.data.data[0] ? response.data.data[0].embed_url : null
            console.log(this.gifUrl)
            return response
      },
  },
  getImage() {
    return this.gifUrl
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
