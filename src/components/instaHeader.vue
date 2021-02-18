<template>
  <header>
      <div class="logoBox">
          <img src="./source/logo.png" class="logo" alt="">
      </div>
  </header>
</template>

<script>
export default {

}
</script>

<style>
header{
    display: block;
    background-color: #fafafa;
    width: 375px;
    height: 50px;
    position: fixed; 
    z-index: 999;
    border-bottom: 1px solid #eee;
}
.logoBox{
    position: absolute; left: 50%; top: 50%;
    transform: translate(-50%, -50%);
}
.logo{
   max-width: 120px;
   display: block;
}
</style>