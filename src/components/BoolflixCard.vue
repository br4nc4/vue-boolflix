<template>
    <div class="card posterCard">
        <img class="card-img-top" :src="posterImage" alt="">
        <div class="card-body overlay">
            <h5 class="card-title">{{htmlTitle}}</h5>
            <p class="card-text text-uppercase"> {{titleCategory}} </p>
            <h5 class="card-title">Country</h5>
            <lang-flag :iso="movie.original_language"/>
            <h5 class="card-title">Vote</h5>

            <MovieRating :vote="movie.vote_average"></MovieRating>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags'; 
import MovieRating from './MovieRating.vue'; 


export default {
    props: {
        movie: Object,
        serie: Object,
    },
    components: {
        LangFlag,
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
        htmlTitle(){
            if (this.movie.name) {
                return "Series Title"
            } else {
                return "Film Title"
            }
        },
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
        background-color: white;
        opacity: 0;
        transition: opacity .2s ease-in-out;
    }

</style>