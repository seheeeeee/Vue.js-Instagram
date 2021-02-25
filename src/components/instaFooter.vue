<template>
  <footer>
      <div class="footer_wrap">
        <div class="homeBox" v-on:click="goHomeFooter">
            <i class="homeBtn fas fa-home fa-lg"></i>
        </div>
        <div class="postBox">
            <input type="file" name="file" id="file" class="inputfile" v-on:change="uploadImage"
                :disabled="step !== 1">
            <label for="file">
                <i class="postBtn far fa-plus-square fa-lg"></i>
            </label>
        </div>
      </div>
  </footer>
</template>

<script>
export default {
    data: function(){
        return {
            step: 1,
            image: "",
        }
    },
    methods: {
        uploadImage: function(evt){ //FileReader API
            const files = evt.target.files;
            if(!files.length) return;//file 없을 경우 return

            const reader = new FileReader();
            reader.readAsDataURL(files[0]);
            reader.onload = evt => {
                this.image = evt.target.result;
                this.step = 2;
                this.$emit('step1', this.image, this.step);
            };
             // To enable reuploading of same files in Chrome
            document.querySelector("#file").value = "";
        },
        goHomeFooter: function(){
            this.$emit('goHomeFooter');
        }
    }
}
</script>

<style>
footer{
    position: sticky; 
    position: -webkit-sticky;
    bottom: 0;
    z-index: 99;
    display: block;
    width: 375px;
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
.inputfile{
    visibility: hidden;
    opacity: 0;
}
</style>