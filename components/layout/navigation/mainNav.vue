<template>
  <transition
    v-on:before-enter="beforeEnter"
    v-on:enter="enter"
    v-on:leave="leave"
    v-bind:css="false"
  >
    <nav :class="uid" v-show="$store.state.navState">
      <ul class="main" @click="$store.dispatch('setNavPayload', false)">
        <li>
          <nuxt-link to="/">home</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/a-page">Our Story</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/dfd">Services</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/a-page">Prices</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/dfd">Stylists</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/a-page">Contact</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/dfd">Book online</nuxt-link>
        </li>
      </ul>
      <slot></slot>
    </nav>
  </transition>
</template>

<script>
  import { gsap } from 'gsap'
  export default {
    props: {
      uid: {
        type: String,
      },
    },
    methods: {
      beforeEnter: function (el) {
        if (el.classList.contains('headerNav')) {
          const mainLi = el.querySelectorAll('.main li')

          gsap.set(el, { opacity: 0, x: '-5%' })
          gsap.set(mainLi, { opacity: 0, x: '-5%' })
        }
      },
      enter: function (el, done) {
        if (el.classList.contains('headerNav')) {
          const mainLi = el.querySelectorAll('.main li')

          let tl = gsap.timeline({ onComplete: done })

          tl.to(el, { opacity: 1, x: 0, duration: 0.2 })
          tl.to(mainLi, { opacity: 1, x: 0, stagger: 0.1 })
        }
      },
      leave: function (el, done) {
        if (el.classList.contains('headerNav')) {
          const mainLi = el.querySelectorAll('.main li')

          let tlq = gsap.timeline({ onComplete: done })

          tlq.to(el, { opacity: 0, x: '-5%', duration: 0.2, ease: 'power3.in' })
        }
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