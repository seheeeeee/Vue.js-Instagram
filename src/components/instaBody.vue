<template>
  <div class="instaBody">
      <div v-if="step === 1" class="feed">
          <insta-post v-for="post in posts" v-bind:post="post" v-bind:key="posts.indexOf(post)"></insta-post>
      </div>
      <div v-if="step === 2">
          <div class="selectedImage" :class="selectedFilter" :style="{ backgroundImage: 'url('+image+')'}">
          </div>
          <div class="filterContainer">
              <filter-type v-for="filter in filters"
                v-bind:filter="filter"
                v-bind:image="image"
                v-bind:key="filters.indexOf(filter)">
              </filter-type>
          </div>
      </div>
      <div v-if="step === 3">
          <div class="selectedImage" :class="selectedFilter" :style="{backgroundImage: 'url('+image+')'}"></div>
          <div class="captionContainer">
              <textarea name="caption" id="caption" class="caption-input" placeholder="Write a caption..."
              v-bind:value="value"
              v-on:input="$emit('input', $event.target.value)"></textarea>
          </div>
      </div>
  </div>
</template>

<script>
import instaPost from './instaPost.vue'
import filterType from './filterType.vue'

export default {
    name: "instaBody",
    props: {
        step: Number,
        posts: Array,
        filters: Array,
        image: String,
        selectedFilter: String,
        value: String
    },
    components: {
        'insta-post': instaPost,
        'filter-type': filterType,
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
    .selectedImage{
        padding-top: 50px;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        height: 330px;
    }
    .filterContainer{
        height: 220px;
        padding: 30px 10px;
        white-space: nowrap;
        overflow-x: scroll;
    }
    .captionContainer{
        height: 210px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .captionContainer textarea{
        border: 0;
        font-size: 1rem;
        width: 100%;
        padding: 10px;
        border-bottom: 1px solid #eee;
    }
    .captionContainer textarea:focus{
        outline: 0;
    }
</style>