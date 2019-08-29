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

    p.author__intro A simple, hackable & minimalistic starter for Gridsome that uses Markdown for content.

    p.author__links
      a(href="//twitter.com/gridsome") Follow on Twitter
      a(href="//github.com/gridsome/gridsome-starter-blog") Github
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<script>
export default {
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
