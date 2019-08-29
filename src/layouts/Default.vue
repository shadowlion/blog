<template lang="pug">
  #app

    header.header
      .header__left
        Logo(v-if="showLogo")
      .header__right
        ToggleTheme

    main.main
      slot

    footer.footer
      span.footer__copyright.d-inline-block Copyright &#169; {{ new Date().getFullYear() }}
</template>

<script>
import { CodeIcon, HeartIcon } from 'vue-feather-icons'
import Logo from '~/components/Logo.vue'
import ToggleTheme from '~/components/ToggleTheme.vue'

export default {
  components: {
    CodeIcon,
    HeartIcon,
    Logo,
    ToggleTheme
  },
  props: {
    showLogo: { default: true }
  }
}
</script>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  padding: 0 calc(var(--space) / 2);
  top:0;
  z-index: 10;

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  @media screen and (min-width: 1300px) {
    //Make header sticky for large screens
    position: sticky;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  padding: 1.5vw 15px 0;
}

.footer {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: calc(var(--space) / 2);
  text-align: center;
  font-size: .8em;

  > span {
    margin: 0 .35em;
  }

  a {
    color: currentColor;
  }
}
</style>
