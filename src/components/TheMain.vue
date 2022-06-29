<template>
    <div>
        <h4>FILMS</h4>
        <div class="row row-cols-5">
            <div class="col" v-for="movie in moviesList" :key="movie.id">
                <BoolflixCard :movie="movie"></BoolflixCard>
            </div>
            <!-- <div id="moviesList">
                <ul class="list-unstyled">
                    <li> <h5>Title</h5> </li>
                    <li v-for="(movie, i) in moviesList" :key="i">{{movie.title}}</li>
                </ul>

                <ul class="list-unstyled">
                    <li> <h5> Vote </h5> </li>
                    <li v-for="(movie, i) in moviesList" :key="i">{{movie.vote_average}}</li>
                </ul>

                <ul class="list-unstyled">
                    <li> <h5> Original Title </h5> </li>
                    <li v-for="(movie, i) in moviesList" :key="i">{{movie.original_title}}</li>
                </ul>

                <ul class="list-unstyled">
                    <li> <h5> Language </h5> </li>
                    <li v-for="(movie, i) in moviesList" :key="i">{{movie.original_language}}</li>
                </ul> 
                <ul class="list-unstyled">
                    <li> <h5>Flag</h5> </li>
                    <li>
                        <lang-flag class="d-flex flex-column" v-for="(movie, i) in moviesList" :key="i" :iso="movie.original_language"/>
                    </li>
                </ul>
            </div> --> 
        </div>

        <div>
            <h4>SERIES</h4>
            <!-- <div id="seriesList">
                <ul class="list-unstyled">
                    <li> <h5>Name</h5> </li>
                    <li v-for="(serie, i) in seriesList" :key="i">{{serie.name}}</li>
                </ul>
            </div> -->
        </div>
    </div>
</template>

<script>
import axios from "axios";
import BoolflixCard from "./BoolflixCard.vue";


export default {
    props: {
        inputText: String,
    },
    components:{
    BoolflixCard
},
    data() {
        return {
            moviesList: [],
            seriesList: [],
        }
    },
    methods: {
        fetchData(type) {
            axios.get("https://api.themoviedb.org/3/search/" + type, {
            params: {
                api_key: "d43e4619fd253e9bace6c00412169652",
                query: this.inputText,
            },
        })
        .then((resp) => {
            if(type === "movie"){
                this.moviesList = resp.data.results;
            } else if (type === "tv") {
                this.seriesList = resp.data.results;
            }
        })
        },
    },
    watch: {
        inputText() {
            this.fetchData("movie")
            this.fetchData("tv")
        }
    }
}
</script>

<style lang="scss">
    #moviesList{
        display: flex;
        gap: 3rem;
    }
    #seriesList{
        display: flex;
    }
</style>