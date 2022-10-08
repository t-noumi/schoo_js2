<template>
  <div id="app">
    <input type="text" v-model="tag" placeholder="タグを入力">
    <input type="button" value="検索" @click="getArticles">
    <ArticleItem
      v-for="(item, index) in articles"
      :key="index"
      :index="index"
      :article="item"
    />
  </div>
</template>

<script>
import axios from 'axios'
import ArticleItem from './components/ArticleItem.vue'
export default {
  name: 'app',
  components: {
    ArticleItem
  },
  data() {
    return {
      articles: [],
      tag: null
    }
  },
  methods: {
    async getArticles() {
      if (this.tag) {
        const res = await axios.get('https://qiita.com/api/v2/items', {
          params: {
            query: `tag:${this.tag}`
          }
        })
        this.articles = res.data
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>