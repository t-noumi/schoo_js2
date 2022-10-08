<template>
  <article>
    <a :href="article.url" target="_blank">
      {{ article.title }}
    </a>
    <div>
      <p>by <strong>{{ article.user.id }}</strong></p>
      <img :src="article.user.profile_image_url" width="20">
    </div>
  </article>
</template>

<script>
export default {
  name: 'ArticleItem',
  props: {
    article: Object
  }
}
</script>
/
<style scoped>
article {
  margin-bottom: 20px;
}
a, div, p, img {
  display: inline-block;
}
a {
  font-size: 20px;
}
div {
  margin-left: 8px;
}
strong {
  font-weight: bold;
}
img {
  margin-left: 4px;
}
</style>