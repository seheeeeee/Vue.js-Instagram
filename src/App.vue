<template>
  <div id="app">
    <div class="app-phone">
      <insta-header :step="step" 
      v-on:goHomeHeader="goHome" 
      v-on:stepUp="stepUpTo3"
      v-on:donePost="sharePost"></insta-header>
      <insta-body 
      v-bind:step="step"
      v-bind:posts="posts" 
      v-bind:filters="filters"
      v-bind:image="image"
      v-bind:selectedFilter="selectedFilter"
      v-model="caption">
      </insta-body>
      <insta-footer v-on:step1="step1" v-on:goHomeFooter="goHome"></insta-footer>
    </div>
  </div>
</template>

<script>
import instaHeader from './components/instaHeader.vue'
import instaBody from './components/instaBody.vue'
import instaFooter from './components/instaFooter.vue'

import posts from './data/post.js'
import filters from './data/filter.js'
import EventBus from './event-bus.js' //부모-자식 사이가 아니여도 자유롭게 사용이 가능함(단, 너무 많이 쓰면 관리 힘듦)

export default {
  components: {
    'insta-header': instaHeader,
    'insta-body': instaBody,
    'insta-footer': instaFooter
  },
  data(){
    return{
      posts,
      filters,
      step: 1,
      image: "",
      selectedFilter: "",
      caption: "",
    }
  },
  methods: {
    step1(image, step){
      this.image = image;
      this.step = step;
    },
    stepUpTo3(){
      this.step = this.step + 1;
    },
    goHome(){
      this.image = "";
      this.selectedFilter = "";
      this.caption = "";
      this.step = 1;
    },
    sharePost(){
      const post = {
        username: "have_a_good_day",
        userImage: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/1211695/vue_lg_bg.png",
        postImage: this.image,
        likes: 0,
        caption: this.caption,
        filter: this.filterType,
      }
      this.posts.unshift(post);
      this.goHome();
    },
    pageHeight(wrap){
      let viewHeight = window.innerHeight;
      return wrap.style.paddingTop = viewHeight*0.2 + 'px';
    },
  },
  created(){
    EventBus.$on("filter-selected", evt => {
      this.selectedFilter = evt.filter;
    });
  },
  mounted(){
    let app = document.getElementById('app');
    this.pageHeight(app)
  },
  
}
</script>

<style scoped>
  *{
    margin: 0; padding: 0;
  }
  body{
    background-color: #fff;
  }
  #app{
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .app-phone{
    width: 375px;
    height: 620px;
    overflow: hidden;
    background-color: #fafafa;
    box-shadow: 0 1px 5px rgba(0,0,0,0.3);
  }
  .homeBtn{
    display: block;
    padding-top: 100px;
  }
</style>