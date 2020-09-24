<template>
  <header>
    <main-nav-btn id="menuBtn" />
    <section id="brand" @click="$store.dispatch('setNavPayload', false)">
      <nuxt-link to="/">
        <logo-1 />
      </nuxt-link>
    </section>
    <anchor id="header_cta" link="/">Book Now!</anchor>
    <main-nav @click="$store.dispatch('setNavPayload', false)" uid="headerNav">
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
  export default {
    mounted() {},
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
    position: absolute;
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
    position: absolute;
    top: 50%;
    right: $headerHeight / 4;
    transform: translateY(-50%);
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