<template lang="pug">
  .author
    g-image.author__image(
      alt="author__image"
      src="~/assets/images/author.jpg"
      width="180"
      height="180"
      blur="5"
    )

    h1.author__site-title(v-if="showTitle") {{ $static.metaData.siteName }}

    p.author__intro Full-stack developer, Ballroom dancer, Google searcher.

    p.author__links
      a(href="//linkedin.com/in/justinchiou")
        linkedin-icon(size="30")
      a(href="//www.youtube.com/channel/UCB3RhejlQaoE2D23zAjFekg")
        youtube-icon(size="30")
      a(href="//github.com/gridsome/gridsome-starter-blog")
        github-icon(size="30")
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<script>
import { GithubIcon, LinkedinIcon, YoutubeIcon } from 'vue-feather-icons'

export default {
  components: { GithubIcon, LinkedinIcon, YoutubeIcon },
  props: ['showTitle']
}
</script>

<style lang="scss">
.author {
  margin: 0 auto;
  max-width: 500px;
  text-align: center;
  padding: calc(var(--space) / 2) 0;

  &__image {
    border-radius: 100%;
    width: 90px;
    height: 90px;
    margin-bottom: 1em;
  }

  &__intro {
    opacity: .8;
  }

  &__site-title {
    font-size: 1.5em;
  }

  &__links {
    margin-top: -.5em;
    a {
      margin: 0 .5em;
    }
  }
}
</style>
