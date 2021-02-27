<template>
  <div>
    <main-header />
    <Nuxt class="page-content-wrapper" />
    <newsletter-sign-up />
    <main-footer />
  </div>
</template>

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
