<template>
  <div class="filterType">
      <p>{{filter.name}}</p>
      <div class="img"
        :class="filter.name"
        :style="{backgroundImage: 'url('+image+')'}"
        v-on:click="selectFilter">
      </div>
  </div>
</template>

<script>
import EventBus from "../event-bus.js"

export default {
    props: {
        filter: Object,
        image: String
    },
    methods: {
        selectFilter: function(){
            EventBus.$emit(
                "filter-selected", { filter : this.filter.name }
            );
        }
    }
}
</script>

<style>
.filterType{
    width: 100px;
    display: inline-block;
    margin: 0 3px;
}
.filterType p{
    font-size: 11px;
    text-align: center;
    text-transform: capitalize;
    padding-bottom: 5px;
}
.filterType .img{
    cursor: pointer;
    width: 100px;
    height: 100px;
    background-size: cover;
    background-position: center;
}
.filterType:last-child{
    margin-right: 20px;
}
</style>