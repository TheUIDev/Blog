<template>
  <v-container fluid="fluid" grid-list-xl="grid-list-xl">
    <v-layout row="row" wrap="wrap">
      <v-flex xs12="xs12" sm12="sm12" md12="md12" lg12="lg12">
        <v-row align="center" justify="center" class="img-row">
          <h1>{{ blog.title }}</h1>
        </v-row>
        <v-row align="center" justify="center" class="img-row">
          <v-img
            :src="blog.photo_url"
            aspect-ratio="1"
            max-width="500"
            max-height="300"
          ></v-img>
        </v-row>
        <v-row align="center" justify="center">
          <social-sharing
            :url="url"
            :title="'❤️ this post - ' + blog.title + ' '"
            :quote="blog.title"
            :hashtags="blog.tags"
            :media="media_url + blog.photo_url"
            twitter-user="shreerangp"
            inline-template
          >
            <v-row align="center" justify="center">
              <div class="social-share">
                <v-btn class="mx-2 mdi mdi-share-variant" dark icon></v-btn>
                Show some ❤️
              </div>
              <network network="facebook">
                <v-btn
                  class="mx-2 mdi mdi-facebook-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="linkedin">
                <v-btn
                  class="mx-2 mdi mdi-linkedin-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="twitter">
                <v-btn
                  class="mx-2 mdi mdi-twitter-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="reddit">
                <v-btn class="mx-2 mdi mdi-reddit social-icons-size" dark icon>
                </v-btn>
              </network>
              <network network="whatsapp">
                <v-btn
                  class="mx-2 mdi mdi-whatsapp social-icons-size"
                  dark
                  icon
                ></v-btn>
              </network>
              <network network="pinterest">
                <v-btn
                  class="mx-2 mdi mdi-pinterest-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="skype">
                <v-btn
                  class="mx-2 mdi mdi-skype social-icons-size"
                  dark
                  icon
                ></v-btn>
              </network>
              <network network="sms">
                <v-btn
                  class="mx-2 mdi mdi-message-text-outline social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="email">
                <v-btn
                  class="mx-2 mdi mdi-email-outline social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
            </v-row>
          </social-sharing>
        </v-row>
        <div class="blogContent" v-html="$md.render(blog.content)"></div>
        <v-row align="center" justify="center">
          <social-sharing
            :url="url"
            :title="'❤️ this post - ' + blog.title + ' '"
            :quote="blog.title"
            :hashtags="blog.tags"
            :media="media_url + blog.photo_url"
            twitter-user="shreerangp"
            inline-template
          >
            <v-row align="center" justify="center">
              <div class="social-share">
                <v-btn class="mx-2 mdi mdi-share-variant" dark icon></v-btn>
                Show some ❤️
              </div>
              <network network="facebook">
                <v-btn
                  class="mx-2 mdi mdi-facebook-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="linkedin">
                <v-btn
                  class="mx-2 mdi mdi-linkedin-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="twitter">
                <v-btn
                  class="mx-2 mdi mdi-twitter-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="reddit">
                <v-btn class="mx-2 mdi mdi-reddit social-icons-size" dark icon>
                </v-btn>
              </network>
              <network network="whatsapp">
                <v-btn
                  class="mx-2 mdi mdi-whatsapp social-icons-size"
                  dark
                  icon
                ></v-btn>
              </network>
              <network network="pinterest">
                <v-btn
                  class="mx-2 mdi mdi-pinterest-box social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="skype">
                <v-btn
                  class="mx-2 mdi mdi-skype social-icons-size"
                  dark
                  icon
                ></v-btn>
              </network>
              <network network="sms">
                <v-btn
                  class="mx-2 mdi mdi-message-text-outline social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
              <network network="email">
                <v-btn
                  class="mx-2 mdi mdi-email-outline social-icons-size"
                  dark
                  icon
                >
                </v-btn>
              </network>
            </v-row>
          </social-sharing>
        </v-row>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      url: window.location.href,
      media_url: window.location.host
    }
  },
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

.social-share {
  margin: 1rem 0;
  font-size: 1.2em;
}

.social-icons-size {
  font-size: 40px;
}
</style>
