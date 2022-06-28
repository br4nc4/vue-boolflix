<template>
  <div>
    <TheHeader @searchMovie="onSearchMovie"></TheHeader>
    <TheMain :text-input="textInput"></TheMain>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import TheMain from './components/TheMain.vue';

export default {
  components: {
    TheHeader,
    TheMain
  },
  data() {
        return {
            textInput: null,
        }
    },
    methods: {
        onSearchMovie(textSearch){
          this.textInput = textSearch;
        }
    },
}
</script>

<style lang="scss">

</style>
