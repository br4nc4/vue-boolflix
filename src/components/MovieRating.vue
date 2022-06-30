<template>
    <div>
        <span v-for="i in 5" :key="i">
            <i v-if="i <= vote5" class="fa-solid fa-star text-warning"></i>
            <i v-else class="fa-regular fa-star"></i>
        </span>
    </div>
</template>

<script>
export default {
    props: {
        vote: Number,
    },
    computed: {
        vote5 () {
            return Math.ceil(this.vote / 2);
        }
    }
}
</script>

<style>

</style>