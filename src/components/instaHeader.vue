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
    width: 100%;
    height: 50px;
    margin: 0 auto;
    position: fixed; 
    z-index: 999;
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