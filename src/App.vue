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

<style lang="stylus" rel="stylesheet/stylus">
  @import "./common/stylus/mixin"
  @import "./common/stylus/base"
  .tab
    display: flex
    width: 100%
    height: 40px
    line-height: 40px
    // border-bottom: 1px solid rgba(7, 17, 27, 0.1)
    border-1px(rgba(7, 17, 27, 0.1))
    .tab-item
      flex: 1
      text-align: center
      & > a
        display: block
        font-size: 14px
        color: rgb(77, 85, 93)
        &.active
          color: rgb(240, 20, 20)
</style>
