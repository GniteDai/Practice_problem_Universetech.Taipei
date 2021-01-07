<template>
  <div class="infinite_outer">
    <div class="loading" v-show="loading">
      <span class="fa fa-spinner fa-spin"></span> Loading
    </div>
    <div v-for="item in items" :key="item">
      <img :src="'https://fakeimg.pl/150x150?text='+item">
    </div>
  </div>
</template>

<script>
export default {
  props: ['items','loading'],
  data: function () {
    return {
      
    }
  },
  mounted () {},
  methods: {}
}
</script>

<style>
  .infinite_outer {
    margin: 5% 0 0;
    width: 100%;
    height: auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  .loading {
    text-align: center;
    position: absolute;
    color: #fff;
    z-index: 9;
    background: purple;
    padding: 8px 18px;
    border-radius: 5px;
    left: calc(50% - 45px);
    top: calc(50% - 18px);
  }  
</style>
