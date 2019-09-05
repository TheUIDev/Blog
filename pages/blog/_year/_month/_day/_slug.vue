<template>
  <v-container fluid="fluid" grid-list-xl="grid-list-xl">
    <v-layout row="row" wrap="wrap">
      <v-flex xs12="xs12" sm12="sm12" md12="md12" lg12="lg12">
        <v-row align="center" justify="center" class="img-row">
          <v-img
            :src="blog.photo_url"
            aspect-ratio="1"
            max-width="500"
            max-height="300"
          ></v-img>
        </v-row>
        <div class="blogContent" v-html="$md.render(blog.content)"></div>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
export default {
  async asyncData({ app, params }) {
    const slug = `${params.year}-${params.month}-${params.day}-${params.slug}`
    const blogposts = await app.$axios.$get('/blogposts.json')
    const blog = blogposts[slug]

    blog.content = blog.content.replace('<!--more-->', '')

    return {
      blog
    }
  }
}
</script>
<style lang="scss">
.img-row {
  margin: 1rem 0;
}

.blogContent img {
  display: block;

  margin: 1rem auto;
}

.blogContent > p > img {
  display: block;
  max-width: 100%;
  height: auto;
}
</style>
