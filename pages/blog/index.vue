<template>
  <v-container fluid="fluid" grid-list-xl="grid-list-xl">
    <v-layout row="row" wrap="wrap">
      <template v-for="(blogpost, idx) in active">
        <v-flex :key="idx" xs12="xs12" sm6="sm6" md4="md4" lg3="lg3">
          <v-card :key="idx" :hover="true">
            <v-img :src="blogpost.photo_url"></v-img>
            <v-card-title primary-title="primary-title">
              <div class="contentCard">
                <h2 class="mb-0">{{ blogpost.title }}</h2>
              </div>
            </v-card-title>
            <v-card-text>
              <div class="date">
                {{ months[new Date(blogpost.date).getMonth()] }}
                {{ new Date(blogpost.date).getDate() }},&nbsp;
                {{ new Date(blogpost.date).getFullYear() }}
              </div>
              <v-chip
                v-for="(tag, tid) in blogpost.tags"
                :key="tid"
                color="success"
                outlined
              >
                {{ tag }}
              </v-chip>
            </v-card-text>
            <v-card-actions>
              <v-btn flat="raised" color="primary" @click="goTo(blogpost.href)"
                >Read more</v-btn
              >
            </v-card-actions>
          </v-card>
          <v-spacer :key="`space-${idx}`"></v-spacer>
        </v-flex>
      </template>
      <v-flex xs12="xs12" md6="md6">
        <InfiniteLoading ref="infiniteLoading" @infinite="onInfinite">
          <p slot="no-more">No more blogposts.</p>
          <p slot="no-results">No more blogposts.</p>
        </InfiniteLoading>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
import InfiniteLoading from 'vue-infinite-loading'
export default {
  layout: 'page',
  components: {
    InfiniteLoading
  },
  data() {
    return {
      months: [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'July',
        'August',
        'September',
        'October',
        'November',
        'December'
      ]
    }
  },
  async asyncData({ app, store }) {
    const data = await app.$axios.$get('/blogposts.json')
    let blogposts = []
    for (const key of Object.keys(data)) {
      const blog = data[key]
      const tmp = key.split('-')
      const date = tmp.slice(0, 3)
      const rest = tmp.slice(3)
      let href = `/blog/${date[0]}/${date[1]}/${date[2]}/${rest.join('-')}`
      href = href.replace('.md', '.html')

      blog.href = href
      blogposts.push(blog)
    }
    blogposts = blogposts.reverse()
    return {
      blogposts,
      active: blogposts.slice(0, 7),
      offset: 0,
      limit: 8
    }
  },
  methods: {
    goTo(link) {
      this.$router.push(link)
    },
    getRndInteger(min, max) {
      return Math.floor(Math.random() * (max - min)) + min
    },
    onInfinite($state) {
      const t = this.getRndInteger(900, 1000)
      setTimeout(() => {
        this.offset = this.offset + this.limit
        const slice = this.blogposts.slice(
          this.offset,
          this.offset + this.limit
        )
        if (slice.length > 0) {
          this.active = this.active.concat(slice)
          $state.loaded()
        } else {
          $state.complete()
        }
      }, t)
    }
  }
}
</script>
<style lang="scss">
.date {
  margin: 1rem 0;
}
</style>
