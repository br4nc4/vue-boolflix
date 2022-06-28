<template>
  <div>
    <TheHeader @searchMovie="onSearchMovie"></TheHeader>
    <TheMain :movies-list="moviesList"></TheMain>
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
            moviesList: [],
        }
    },
    methods: {
        fetchData(searchText) {
            axios.get("https://api.themoviedb.org/3/search/movie", {
            params: {
                api_key: "d43e4619fd253e9bace6c00412169652",
                query: searchText,
            },
        })
        .then((resp) => {
            this.moviesList.push(...resp.data.results);
        })
        
        },
        onSearchMovie(searchText){
          this.fetchData(searchText)
        }
    },
    mounted() {
        this.fetchData()
    }
}
</script>

<style lang="scss">

</style>
