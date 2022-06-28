<template>
    <form class="input-group mb-3">
        <input type="text" class="form-control"
        placeholder="search movie" 
        aria-describedby="button-addon2"
        v-model="searchText">
        <button class="btn btn-outline-secondary" type="button" 
        id="button-addon2"
        @click="onSearchClick">Search</button>
    </form>
</template>

<script>


export default {
    components: {
    },
    data() {
        return {
            searchText: "",
        }
    },
    methods: {
        onSearchClick() {
            this.$emit("searchMovie", this.searchText);
        }
    },
}
</script>

<style lang="scss">

</style>