<template>
    <div class="card">
        <img class="card-img-top" :src="posterImage" alt="">
        <div class="card-body">
            <h5 class="card-title">Film Title</h5>
            <p class="card-text text-uppercase">{{movie.title}}</p>
            <h5 class="card-title">Country</h5>
            <lang-flag :iso="movie.original_language"/>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    props: {
        movie: Array,
    },
    components: {
        LangFlag,
    },
    data() {
        return {
            imgUrl: "https://image.tmdb.org/t/p/",
            imgDim: "w185",
            imgPath: this.movie.poster_path,
        }
    },
    computed: {
        posterImage() {
            return this.imgUrl + this.imgDim + this.imgPath;
        }
    }
}
</script>

<style lang="scss">

</style>