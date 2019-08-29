<template lang="pug">
  layout
    h1.tag-title.text-center.space-bottom # {{ $page.tag.title }}

    .posts
      post-card(
        v-for="edge in $page.tag.belongsTo.edges"
        :key="edge.node.id"
        :post="edge.node"
      )
</template>

<page-query>
query Tag ($id: String!) {
  tag (id: $id) {
    title
    belongsTo {
      edges {
        node {
          ...on Post {
            title
            path
            date (format: "D. MMMM YYYY")
            timeToRead
            description
            content
          }
        }
      }
    }
  }
}
</page-query>

<script>
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'

export default {
  components: {
    Author,
    PostCard
  },
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style lang="scss">

</style>

