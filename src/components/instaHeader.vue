<template>
  <header>
      <div class="logoBox">
          <img src="./source/logo.png" class="logo" alt="">
          <a class="cancelBtn" v-if="step === 2 || step === 3"
            v-on:click="goHomeHeader">Cancel</a>
          <a class="nextBtn" v-if="step === 2" v-on:click="stepUp">Next</a>
          <a class="doneBtn" v-if="step === 3" @click="donePost">Done</a>
      </div>
  </header>
</template>

<script>
export default {
    props: ['step'],
    data: function(){
        return {
            step3: 3,
        }
    },
    methods: {
        goHomeHeader: function(){
            this.$emit('goHomeHeader');
        },
        stepUp: function(){
            this.$emit('stepUp', this.step3);
        },
        donePost: function(){
            this.$emit('donePost');
        }
    },

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
   position: relative;
}
.logo{
     position: absolute; left: 50%; top: 12px;
    transform: translate(-50%, 0);
   max-width: 120px;
   display: block;
}
.cancelBtn, .nextBtn, .doneBtn{
    position: absolute; top: 12px;
    color: #209cee;
    font-weight: bold;
    cursor: pointer;
}
.cancelBtn{
    left: 10px;
}
.nextBtn, .doneBtn{
    right: 10px;
}
</style>