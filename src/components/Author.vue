<template>
  <div class="author">
    <g-image
      alt="Author image"
      class="author__image"
      src="~/assets/images/author.jpg"
      width="180"
      height="180"
      blur="5"
    />

    <h1 v-if="showTitle" class="author__site-title">
      {{ $static.metadata.siteName }}
    </h1>

    <p class="author__intro">
      Fullstack developer
      <a href="https://wunderfund.co">@Wunderfund</a>, ballroom dancer, problem
      solver.
    </p>

    <p class="author__links">
      <a
        href="https://linkedin.com/in/justinchiou"
        target="_blank"
        name="linkedin"
        >LinkedIn</a
      >
      <a
        href="https://www.youtube.com/channel/UCB3RhejlQaoE2D23zAjFekg"
        target="_blank"
        name="youtube"
        >Youtube</a
      >
      <a href="https://github.com/shadowlion" target="_blank" name="github"
        >Github</a
      >
      <a href="https://gitlab.com/shadowlion" target="_blank" name="gitlab"
        >Gitlab</a
      >
      <a href="mailto:chiou.kai@gmail.com" name="email">Email</a>
    </p>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
export default {
  props: ["showTitle"],
};
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
    opacity: 0.8;
  }

  &__site-title {
    font-size: 1.5em;
  }

  &__links {
    margin-top: -0.5em;
    a {
      margin: 0 0.5em;
    }
  }
}
</style>
