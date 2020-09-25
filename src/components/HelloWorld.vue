<template>
  <div>
      <button @click="getitem">test</button>
<br>
      word : {{word}} 
      <br>
      mean : {{mean}}
      <br>
      partOfSpeech : {{partOfSpeech}}
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            word:'',
            mean:'',
            partOfSpeech:''

        }

        
    },

    methods:{
        getitem(){
            axios.get('https://api.dictionaryapi.dev/api/v2/entries/en/hello')
            .then(res => {
                this.word = res.data[0].word
                this.mean = res.data[0].meanings[0].definitions[0].definition
                this.partOfSpeech = res.data[0].meanings[0].partOfSpeech
                console.log(res.data)
            })
            .catch(err => {
                console.error(err); 
            })
        }
    }
}
</script>

<style>

</style>