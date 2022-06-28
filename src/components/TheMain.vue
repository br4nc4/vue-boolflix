<template>
    <div>
        <div id="moviesList"> 
            <!-- STAMPARE CARD PER OGNI FILM -->
            <ul class="list-unstyled">
                <li>{{textInput}}</li>
            </ul>
        </div>

        <div id="seriesList">

        </div>
    </div>
</template>

<script>
export default {
    components: {
    },
    props: {
        textInput: String,
    },
}
</script>

<style lang="scss">

</style>