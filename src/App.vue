<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <router-view></router-view>
  </div>
</template>

<script>
import Header from './components/header/header';
const ERR_OK = 0;
export default {
  data() {
    return {
      seller: {}
    };
  },
  components: {
    'v-header': Header
  },
  created() {
    this.$http.get('/api/seller').then((response) => {
      if (response.data.errno === ERR_OK) {
        this.seller = response.data.data;
      }
    });
  },
  name: 'app'
};
</script>

<style>

</style>
