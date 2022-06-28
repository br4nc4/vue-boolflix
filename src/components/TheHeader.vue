<template>
    <div class="input-group mb-3">
        <input type="text" class="form-control"
        placeholder="search movie" 
        aria-describedby="button-addon2"
        v-model="onInput">
        <button class="btn btn-outline-secondary" type="button" 
        id="button-addon2"
        @click="onSearchClick">search</button>
    </div>
</template>

<script>

export default {
    components: {
    },
    data() {
        return {
            onInput: "",
        }
    },
    methods: {
        onSearchClick() {
            this.$emit("searchMovie", this.onInput);
        }
    },
}
</script>

<style lang="scss">

</style>