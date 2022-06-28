<template>
    <div>
        <div id="moviesList"> 
            <!-- STAMPARE CARD PER OGNI FILM -->
            <ul class="list-unstyled">
                <li v-for="(movie, i) in moviesList" :key="i">{{movie.title}}</li>
            </ul>
        </div>

        <div id="seriesList">

        </div>
    </div>
</template>

<script>

export default {
    props: {
        moviesList: Object,
    },
}
</script>

<style lang="scss">

</style>