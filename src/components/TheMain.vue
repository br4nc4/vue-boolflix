<template>
    <div>
        <div id="moviesList"> 
            <!-- STAMPARE CARD PER OGNI FILM -->
            <ul class="list-unstyled">
                <li v-for="(movie, i) in moviesList" :key="i">{{movie.title}}</li>
                <li v-for="(movie, i) in moviesList" :key="i">{{movie.vote_average}}</li>
            </ul>
        </div>

        <div id="seriesList">

        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
    props: {
        textInput: String,
    },
    data() {
        return {
            moviesList: [],
        }
    },
    methods: {
        searchData(textInput) {
            axios.get("https://api.themoviedb.org/3/search/movie", {
            params: {
                api_key: "d43e4619fd253e9bace6c00412169652",
                query: textInput,
            },
        })
        .then((resp) => {
            this.moviesList.push(...resp.data.results);
        })
        
        }
    },
    mounted() {
        this.searchData("futuro")
    }
}
</script>

<style lang="scss">

</style>