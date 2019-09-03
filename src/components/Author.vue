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

    p.author__intro Fullstack developer
      |
      |
      | @
      <a href="https://wunderfund.co">Wunderfund</a>
      |, ballroom dancer, Google-searching problem solver.

    p.author__links
      a(href="https://linkedin.com/in/justinchiou" target="_blank")
        linkedin-icon(size="30")
      a(
        href="https://www.youtube.com/channel/UCB3RhejlQaoE2D23zAjFekg" target="_blank"
      )
        youtube-icon(size="30")
      a(href="https://github.com/shadowlion" target="_blank")
        github-icon(size="30")
      a(href="https://gitlab.com/shadowlion" target="_blank")
        gitlab-icon(size="30")
      a(href="mailto:chiou.kai@gmail.com")
        mail-icon(size="30")
      a(href="tel:6302048122" target="_blank")
        phone-icon(size="30")
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<script>
import {
  GithubIcon, GitlabIcon, LinkedinIcon, YoutubeIcon, MailIcon, PhoneIcon
} from 'vue-feather-icons'

export default {
  components: {
    GithubIcon,
    GitlabIcon,
    LinkedinIcon,
    YoutubeIcon,
    MailIcon,
    PhoneIcon
  },
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
    // margin-top: -.5em;
    a {
      margin: 0 .5em;
    }
  }
}
</style>
