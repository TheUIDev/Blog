<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <div class="text-xs-center" />
      <v-card class="justify-center">
        <div class="text-center">
          <v-avatar :size="150">
            <img src="/blog-author.jpg" alt="Shree" />
          </v-avatar>
        </div>
        <v-card-title class="headline justify-center primary--text">
          Shreerang Patwardhan
        </v-card-title>
        <v-card-text class="justify-center white--text">
          <v-row justify="center" class="author-social">
            <a href="https://twitter.com/shreerangp" target="_blank">
              <v-icon large class="mx-4">mdi-twitter</v-icon>
            </a>
            <a href="https://linkedin.com/in/shreerangp" target="_blank">
              <v-icon large class="mx-4">mdi-linkedin</v-icon>
            </a>
          </v-row>
          <p>
            <strong>
              Software Engineering Manager
            </strong>
            @
            <strong>
              Williams Sonoma Inc.
            </strong>
            leading the Registry, Product Selection & Discovery Domains.
          </p>
          <h3 class="author-listing">
            <v-btn class="mx-2" fab dark small color="red">
              <v-icon dark>mdi-school</v-icon>
            </v-btn>
            Computer Science Engineer
          </h3>
          <h3 class="author-listing">
            <v-btn class="mx-2" fab dark small color="pink">
              <v-icon dark>mdi-school</v-icon>
            </v-btn>
            Certified Scrum Master
          </h3>
          <h3 class="author-listing">
            <v-btn class="mx-2" fab dark small color="purple">
              <v-icon dark>mdi-pen</v-icon>
            </v-btn>
            Author
          </h3>
          <div class="book-holder">
            <iframe
              type="text/html"
              width="250"
              height="418"
              frameborder="0"
              allowfullscreen
              style="max-width:100%"
              src="https://read.amazon.com/kp/card?asin=B00YSIKTMY&preview=newtab&linkCode=kpe&ref_=cm_sw_r_kb_dp_KggDDbMSTWEEG"
            ></iframe>
          </div>
          <h3 class="author-listing">
            <v-btn class="mx-2" fab dark small color="green">
              <v-icon dark>mdi-thought-bubble-outline</v-icon>
            </v-btn>
            Random Writings -
            <a href="https://www.quora.com/profile/Shreerang-Patwardhan">
              Quora
            </a>
          </h3>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {}
</script>
<style lang="scss" scoped>
.author-listing {
  margin: 1rem 0;
}

.author-social {
  padding: 0.5rem 0 1rem 0;
}

.author-social a {
  text-decoration: none;
  cursor: pointer;
}
.book-holder {
  text-align: center;
}
</style>
