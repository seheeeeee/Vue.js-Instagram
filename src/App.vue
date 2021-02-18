<template>
  <div id="app">
    <insta-header></insta-header>
    <insta-body v-bind:posts="posts" v-bind:filters="filters"></insta-body>
    <insta-footer></insta-footer>
  </div>
</template>

<script>
import instaHeader from './components/instaHeader.vue'
import instaBody from './components/instaBody.vue'
import instaFooter from './components/instaFooter.vue'

import posts from './data/post.js'
import filters from './data/filter.js'

export default {
  data: function(){
    return{
      posts,
      filters,
    }
  },
  components: {
    'insta-header': instaHeader,
    'insta-body': instaBody,
    'insta-footer': instaFooter
  }
}
</script>

<style scoped>
  body{
    background-color: #fff;
  }
  #app{
    position: relative;
  }
</style>