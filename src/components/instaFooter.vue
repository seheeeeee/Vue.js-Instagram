<template>
  <footer>
      <div class="footer_wrap">
        <div class="homeBox">
            <i class="homeBtn fas fa-home fa-lg"></i>
        </div>
        <div class="postBox">
            <i class="postBtn far fa-plus-square fa-lg"></i>
        </div>
      </div>
  </footer>
</template>

<script>
export default {

}
</script>

<style>
footer{
    position: fixed; left: 0; bottom: 0;
    /* position: -webkit-sticky; */
    z-index: 99;
    display: block;
    width: 100%;
    height: 35px;
    background-color: #fafafa;
    border-top: 1px solid #eee;
}
.footer_wrap{
    max-width: 740px;
}
.homeBox{
    position: absolute; left: 10px; top: 6px;
}
.postBox{
    position: absolute; right: 10px; top: 6px;
}
</style>