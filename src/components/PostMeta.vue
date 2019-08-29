<template lang="pug">
  .post-meta
    span Posted {{ post.date }}.
    template(v-if="post.timetoRead")
      strong {{ post.timeToRead }} min read.
</template>

<script>
export default {
  props: ['post']
}
</script>

<style lang="scss">
.post-meta {
  font-size: .8em;
  opacity: .8;
}
</style>
