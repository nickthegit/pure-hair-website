<template>
  <header>
    <main-nav-btn id="menuBtn" />
    <section id="brand" @click="$store.dispatch('setNavPayload', false)">
      <nuxt-link to="/">
        <logo-1 />
      </nuxt-link>
    </section>
    <a href id="header_cta">Book Now!</a>
    <main-nav
      v-show="$store.state.navState"
      @click="$store.dispatch('setNavPayload', false)"
      uid="headerNav"
    >
      <socials uid="headerSocials" />
    </main-nav>
    <div
      id="nav_white-space"
      v-show="$store.state.navState"
      @click="$store.dispatch('setNavPayload', false)"
    ></div>
  </header>
</template>

<script>
  import { gsap } from 'gsap'
  export default {
    head() {
      return {
        bodyAttrs: {
          class: this.$store.state.navState ? 'navOpen' : 'navClosed',
        },
      }
    },
  }
</script>

<style lang="scss" scoped>
  header {
    position: relative;
    z-index: 999999;
    top: 0;
    left: 0;
    width: 100%;
    height: $headerHeight;
    background: $white;
  }
  #menuBtn {
    position: absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
  }
  #brand {
    display: flex;
    position: relative;
    height: $headerHeight / 2;
    width: 100%;
    left: 0;
    top: $headerHeight / 4;
    z-index: 5;
    margin: 0 auto;
    a {
      height: 100%;
      position: relative;
      margin: 0 auto;
    }
    svg {
      height: 100%;
      fill: $primary;
    }
  }
  #header_cta {
    display: flex;
    color: $white;
    background: $primary;
    text-decoration: none;
    text-transform: uppercase;
    font-size: 14px;
    line-height: 14px;
    font-weight: 700;
    position: absolute;
    top: 50%;
    right: $headerHeight / 4;
    transform: translateY(-50%);
    padding: 16px 25px 12px 25px;
    border-radius: 20px;
    text-align: center;
    z-index: 5;
    @include breakpoint(mobile) {
      position: fixed;
      top: unset;
      right: unset;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
    }
  }
  #mainNav {
  }
  #nav_white-space {
    width: 66.6666666%;
    height: 100vh;
    background: transparent;
    z-index: 4;
    top: 0;
    position: absolute;
    right: 0;
    @include breakpoint(tablet) {
      width: 33.333333%;
    }
    @include breakpoint(mobile) {
      width: 10%;
    }
  }
  .navOpen {
    .menu-btn {
      color: $white;
    }
    #brand {
      svg {
        // fill: $white;
      }
    }
  }
</style>