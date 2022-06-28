<template>
  <div>
    <TheHeader @searchMovie="onSearchMovie"></TheHeader>
    <TheMain :text-input="textInput"></TheMain>
  </div>
</template>

<script>
import axios from "axios";
import TheHeader from './components/TheHeader.vue';
import TheMain from './components/TheMain.vue';

export default {
  components: {
    TheHeader,
    TheMain
  },
  data() {
        return {
            movieList: [],
            textInput: null,
        }
    },
    methods: {
        fetchData() {
            axios.get("https://api.themoviedb.org/3/search/movie", {
                params: {
                    api_key: "d43e4619fd253e9bace6c00412169652",
                    /* query: textSearch, */
                },
            })
            .then((resp) => {
                this.movieList = resp.data.results;
            })
        },
        onSearchMovie(textSearch){
          this.textInput = textSearch;
        }
    },
    mounted() {
        this.fetchData();
    }
}
</script>

<style lang="scss">

</style>
