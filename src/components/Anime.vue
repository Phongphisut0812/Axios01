<template>
  <div class="containr">
    <!-- <input type="text" v-model="keyword" /> -->
    <button class="btn btn-outline-warning " @click="searchData()">Search </button>
    {{result}} 

     
        <b-card
          v-if = "result" 
          :title="result.word"
          tag="article"
          style="max-width: 20rem;"
          class="mb-2"
        >
          <b-card-text>{{data.meanings.definitions.definition}}</b-card-text> 

          <b-button href="data.url" variant="primary">Go somewhere</b-button>
        </b-card>
       
    </div>
   
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      result: null,
      keyword: "",
    };
  },
  methods: {
    searchData() {
      axios
        .get("https://api.dictionaryapi.dev/api/v2/entries/en/hello" )
        .then((response) => {
          this.result = response.data;
           console.log(this.result);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>
</style>
