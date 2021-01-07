<template>
  <div class="list_outer">
    <div v-for="(item, index) in repoList" :key="index" class="item">
      <div class="name" v-text="item.name" />
      <a :href="item.html_url" class="url" v-text="item.html_url" />
      <div class="desc" v-text="item.description" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data: function () {
    return {
      base: "https://api.github.com/users",
      username: 'GniteDai',
      repoList: null
    }
  },
  created() {},
  mounted() {
    this.getRepos()
  },
  methods: {
    async getRepos(){
      const res = (await axios.get(`${this.base}/${this.username}/repos`)).data
      this.repoList = res
    }
  }
}
</script>

<style>
  .list_outer{
    width: 100%;
    height: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .item {
    width: 50vw;
    height: auto;
    border: 1px solid white;
    text-align: center;
    margin: 1%;
  }
  .name {
    font-size: 32px;
    color: cadetblue;
  }
  .url {
    font-size: 18px;
    color: bisque;
  }
  .desc {
    font-size: 20px;
    color: darkgoldenrod;
  }
</style>
