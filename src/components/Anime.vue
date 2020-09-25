<template>
  <div class="containr">
    <input type="text" v-model="keyword" />
    <button class="btn btn-outline-warning" @click="search()">Search</button>
    <!-- <br />
    word : {{ word }}
    <br />
    mean : {{ mean }}
    <br />
    partOfSpeech : {{ partOfSpeech }} -->
    <div class="row">
      <div class="col-md-10 box"> 
        <b-card
          :title="word"
          :sub-title="partOfSpeech"
          style="max-width: 50rem"
          tag="article"
          class="mb-2 mt-5" 
        >
          <b-card-text>
            {{ mean }}
          </b-card-text>
          <!-- <b-link href="#" class="card-link">Another link</b-link> -->
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      word: "",
      mean: "",
      partOfSpeech: "",
      keyword: "",
    };
  },
  methods: {
    search() {
      axios
        .get("https://api.dictionaryapi.dev/api/v2/entries/en/" + this.keyword)
        .then((res) => {
          this.word = res.data[0].word;
          this.mean = res.data[0].meanings[0].definitions[0].definition;
          this.partOfSpeech = res.data[0].meanings[0].partOfSpeech;
          console.log(res.data);
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style>
.box {
  margin-left: auto;
}
</style>
