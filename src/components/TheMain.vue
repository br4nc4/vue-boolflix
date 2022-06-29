<template>
    <div>
        <div id="moviesList"> 
            <!-- STAMPARE CARD PER OGNI FILM -->
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
                <li> <h5> Original Language </h5> </li>
                <li v-for="(movie, i) in moviesList" :key="i">{{movie.original_language}}</li>
            </ul>
        </div>

        <div id="seriesList">

        </div>
    </div>
</template>

<script>

export default {
    props: {
        moviesList: Array,
    },
}
</script>

<style lang="scss">
    #moviesList{
        display: flex;
        gap: 3rem;
    }
</style>