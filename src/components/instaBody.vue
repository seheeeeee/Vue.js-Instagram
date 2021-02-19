<template>
  <div class="instaBody">
      <div v-if="step === 1" class="feed">
          <insta-post v-for="post in posts" v-bind:post="post" v-bind:key="posts.indexOf(post)"></insta-post>
      </div>
  </div>
</template>

<script>
import instaPost from './instaPost.vue'

export default {
    name: "instaBody",
    props: {
        step: Number,
        posts: Array,
        filters: Array,
        image: String,
    },
    components: {
        'insta-post': instaPost
    }
}
</script>

<style>
    .instaBody{
        height: 100%;
    }
    .feed{
        height: 100%;
        overflow-x: hidden;
        overflow-y: scroll;
        margin-right: -15px;
    }
</style>