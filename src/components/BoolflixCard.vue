<template>
    <div class="card posterCard">
        <img class="card-img-top" :src="posterImage" alt="">
        <div class="card-body overlay overflow-auto">
            <p class="text-white fw-bold mb-0">Title: 
                <span class="text-white fw-normal"> {{titleCategory}} </span> 
            </p>
            <p class="text-white fw-bold mb-0">Original Title: 
                <span class="text-white fw-normal"> {{originalTitleCategory}} </span> 
            </p>
            <div class="d-flex">
                <p class="text-white fw-bold mb-0">Vote: </p>
                <MovieRating :vote="movie.vote_average"></MovieRating>
            </div>
            <p class="text-white fw-bold mb-0 lh-1">Overview: 
                <span class="text-white fw-normal"> {{movie.overview}} </span> 
            </p>
            <!-- <h5 class="card-title text-white">Country</h5>
            <lang-flag :iso="movie.original_language"/> -->
        </div>
    </div>
</template>

<script>
/* import LangFlag from 'vue-lang-code-flags'; */ 
import MovieRating from './MovieRating.vue'; 


export default {
    props: {
        movie: Object,
        serie: Object,
    },
    components: {
        /* LangFlag, */
        MovieRating, 
},
    data() {
        return {
            imgUrl: "https://image.tmdb.org/t/p/",
            imgDim: "w185",
            imgPath: this.movie.poster_path,
            errorImg: "/img/noimage.jpg",
        }
    },
    computed: {
        posterImage() {
            if(!this.imgPath){
                return this.errorImg;
            }
            return this.imgUrl + this.imgDim + this.imgPath;
        },
        titleCategory(){
            if (this.movie.name) {
                return this.movie.name;
            } 
            return this.movie.title;
        },
        originalTitleCategory() {
            if (this.movie.original_name) {
                return this.movie.original_name;
            }
            return this.movie.original_title;
        }
        /* htmlTitle(){
            if (this.movie.name) {
                return "Series Title"
            } else {
                return "Film Title"
            }
        }, */
    },
}
</script>

<style lang="scss">
    .posterCard{
        position: relative;
        &:hover{
            .card-body.overlay{
                opacity: 1;
            }
        }
    }

    .card-body.overlay{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: black;
        opacity: 0;
        transition: opacity .2s ease-in-out;
    }

</style>