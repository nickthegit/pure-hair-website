<template>
  <div>
    <main-header />
    <Nuxt class="page-content-wrapper" />
    <newsletter-sign-up />
    <main-footer />
  </div>
</template>

<script>
import MainFooter from '~/components/layout/mainFooter.vue'
import mainHeader from '~/components/layout/navigation/mainHeader.vue'
import NewsletterSignUp from '~/components/newsletter/newsletterSignUp.vue'
export default {
  components: { mainHeader, MainFooter, NewsletterSignUp },
}
</script>

<style lang="scss">
div {
  width: 100%;
  overflow-x: hidden;
}
.page-content-wrapper {
  width: 100%;
  min-height: 80vh;
  transition: transform 0.2s ease-out;
  transition-delay: 0.1s;
}
.navOpen {
  .page-content-wrapper {
    transform: translateX(5%);
  }
}
</style>
