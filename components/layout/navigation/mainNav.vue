<template>
  <nav :class="uid">
    <ul class="main" @click="$store.dispatch('setNavPayload', false)">
      <li>
        <nuxt-link to="/">home</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/a-page">a page</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/dfd">404</nuxt-link>
      </li>
    </ul>
    <slot></slot>
  </nav>
</template>

<script>
  export default {
    props: {
      uid: {
        type: String,
      },
    },
  }
</script>

<style lang="scss" scoped>
  .headerNav {
    padding-top: $headerHeight;
    position: absolute;
    width: 33.333333%;
    height: 100vh;
    top: 0;
    left: 0;
    z-index: 5;
    background: $primary;
    background: linear-gradient(
      180deg,
      rgba(17, 34, 107, 1) 0%,
      rgba(9, 19, 59, 1) 100%
    );
    // #09133b
    display: block;
    @include breakpoint(tablet) {
      width: 66.66666%;
    }
    @include breakpoint(mobile) {
      width: 90%;
    }
    .main {
      padding: 40px;
      a {
        display: block;
        padding: 10px;
        text-decoration: none;
        color: $white;
        font-family: 'Permanent Marker', cursive;
        font-size: 5vh;
      }
    }
  }
</style>