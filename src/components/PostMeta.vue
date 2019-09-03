<template lang="pug">
  .post-meta
    span Posted {{ post.date }}
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
