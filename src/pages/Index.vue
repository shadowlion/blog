<template lang="pug">
  layout(:show-logo="false")
    author(:show-title="true")
    .posts
      post-card(
        v-for="edge in $page.posts.edges"
        :key="edge.node.id"
        :post="edge.node"
      )
</template>

<page-query>
{
  posts: allPost(filter: { published: { eq: true }}) {
    edges {
      node {
        id
        title
        path
        tags {
          id
          title
          path
        }
        date (format: "D. MMMM YYYY")
        timeToRead
        description
        coverImage (width: 770, height: 380, blur: 10)
        ...on Post {
            id
            title
            path
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
  // },
  // metaInfo: {
  //   title: 'Welcome'
  }
}
</script>
