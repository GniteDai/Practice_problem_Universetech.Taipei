<template>
  <div class="outer" id="infinite-list" @scroll="handleScroll">
    <gitHubRepoList />
    <hr style="color: white; width: 100%;">
    <infiniteScroll :items="items" :loading="loading" />
  </div>
</template>

<script>
import gitHubRepoList from '~/components/github_repo_list.vue';
import infiniteScroll from '~/components/Infinite_Scroll.vue';
export default {
  components: {
    gitHubRepoList,
    infiniteScroll
  },
  data: function () {
    return {
      loading: false,
      nextItem: 1,
      items: []
    }
  },
  mounted(){
    this.loadMore();
  },
  methods: {
    handleScroll(){
      const listElm = document.querySelector('#infinite-list');
      if(listElm.scrollTop + listElm.clientHeight >= listElm.scrollHeight) {
        this.loadMore();
      }
    },
    loadMore () {
      this.loading = true;
      setTimeout(e => {
        for (var i = 0; i < 10; i++) {
          this.items.push('Picture ' + this.nextItem++);
        }
        this.loading = false;
      }, 200);
    }
  }
}
</script>

<style>
  .outer{
    padding: 1% 0 0;
    width: 100%;
    height: 100vh;
    overflow: auto;
    background-color: rgb(24, 26, 27);
  }
</style>
