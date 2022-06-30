<template>
    <div class="bgHeader p-2">
        <form class="d-flex justify-content-between align-items-center">
            <img class="logoDim" src="/img/logo.png" alt="">
            <div class="d-flex input-group-sm h-50">
                <input type="text" class="form-control"
                placeholder="search movies and series" 
                aria-describedby="button-addon2 inputGroup-sizing-sm"
                v-model="searchText">
                <button class="btn btn-primary" type="button" 
                id="button-addon2"
                @click="onSearchClick">Search</button>
            </div>
        </form>
    </div>
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
    .logoDim{
        width: 150px;
        height: 50px;
    }
    .bgHeader{
        background-color: black;
    }
</style>