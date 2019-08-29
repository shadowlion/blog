<template lang="pug">
  .post-card.content-box(:class="{ 'post-card--has-poster' : post.poster }")

    .post-card__header
      g-image.post-card__image(
        alt="Cover image"
        v-if="post.coverImage"
        :src="post.coverImage"
      )

    .post-card__content
      h2.post-card__title(v-html="post.title")
      p.post-card__description(v-html="post.description")

      post-meta.post-card__meta(:post="post")
      post-tags.post-card__tags(:post="post")

      g-link.post-card__link(:to="post.path") Link
</template>

<script>
import PostMeta from '~/components/PostMeta'
import PostTags from '~/components/PostTags'

export default {
  components: {
    PostMeta,
    PostTags
  },
  props: ['post'],
}
</script>

<style lang="scss">
.post-card {
  margin-bottom: var(--space);
  position: relative;

  &__header {
    margin-left: calc(var(--space) * -1);
    margin-right: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    margin-top: calc(var(--space) * -1);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    &:empty {
      display: none;
    }
  }

  &__image {
    min-width: 100%;
  }

  &__title {
    margin-top: 0;
  }

  &:hover {
    transform: translateY(-5px);
    box-shadow: 1px 10px 30px 0 rgba(0,0,0,.1);
  }

  &__tags {
    z-index: 1;
    position: relative;
  }

  &__link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0.0;
    overflow: hidden;
    text-indent: -9999px;
    z-index: 0;
  }
}
</style>
