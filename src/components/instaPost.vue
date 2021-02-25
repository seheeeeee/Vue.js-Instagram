<template>
  <div class="instaPost">
      <div class="header level">
          <div class="level-left">
              <figure class="image is-32x32">
                <img v-bind:src="post.userImage" alt="">
              </figure>
            <span class="userName">{{post.username}}</span>
          </div>
      </div>
      <div class="imageContainer" 
        v-bind:class="post.filter" 
        v-bind:style="{backgroundImage: 'url('+post.postImage+')'}"
        v-on:dblclick="like">
      </div>
      <div class="content">
          <div class="heart">
              <i class="far fa-heart fa-lg"
              v-bind:class="{'fas':this.post.hasBeenLiked}"
              v-on:click="like"></i>
          </div>
          <p class="likes">{{post.likes}} likes</p>
          <p class="caption">
              <span>{{post.username}}</span> {{post.caption}}
          </p>
      </div>
  </div>
</template>

<script>
export default {
    name: "instaPost",
    props: {
        post: Object,
    },
    methods:{
        like: function(){
            if(this.post.hasBeenLiked){
                this.post.likes--;
            }else{
                this.post.likes++;
            }
            this.post.hasBeenLiked = !this.post.hasBeenLiked; //false -> true.
        }
    }
}
</script>

<style scoped>
    .instaPost{
        padding-top: 50px;
    }
    .instaPost:last-child{
        margin-bottom: 80px;
    }
    .header{
        height: 30px;
        border-bottom: 1px solid #fff;
        margin: 7.5px 10px;
    }
    .image{
        display: inline-block;
    }
    img{
        border-radius: 50%;
        width: 32px;
        height: 32px;
    }
    .userName{
        position: relative; top: -3px;
        padding-left: 7px;
        font-size: 0.9rem;
        font-weight: bold;
    }
    .level{
        margin-bottom: 0.5rem !important;
    }
    .imageContainer{
        height: 330px;
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
    }
    .content{
        margin: 7.5px 10px;
    }
    .far.fa-heart,
    .fas.fa-heart{
        cursor: pointer;
    }
    .fas.fa-heart{
        color: #f06595;
    }
    .likes{
        margin: 5px 0;
        font-size: 0.85rem;
        font-weight: bold;
    }
    .caption{
        font-size: 0.85rem;
    }
    .caption span{
        font-weight: bold;
    }
</style>