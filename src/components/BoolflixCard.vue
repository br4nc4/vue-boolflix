<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">Film title</h5>
            <p class="card-text">{{movie.title}}</p>
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
    }
}
</script>

<style lang="scss">

</style>