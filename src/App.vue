<template>
  <div>
    <div class="container">
      <TheHeader @searchMovie="onSearchMovie"></TheHeader>
      <TheMain :input-text="inputText"></TheMain>
    </div>
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
            inputText:"",
        }
    },
    methods: {
        onSearchMovie(searchText){
          this.inputText = searchText;
        }
    },
}
</script>

<style lang="scss">
  @import "assets/scss/main.scss";
</style>
