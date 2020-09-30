<template>
  <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @leave="leave"
    @leave-cancelled="leaveCancelled"
    :css="false"
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
          gsap.set(mainLi, { opacity: 0, y: 20 })
        }
      },
      enter: function (el, done) {
        if (el.classList.contains('headerNav')) {
          const mainLi = el.querySelectorAll('.main li')

          let tl = gsap.timeline({ onComplete: done })

          tl.to(el, { opacity: 1, x: 0, duration: 0.2 })
          tl.to(mainLi, { opacity: 1, y: 0, stagger: 0.1 }, '-=0.1')
        }
      },
      leave: function (el, done) {
        if (el.classList.contains('headerNav')) {
          const mainLi = el.querySelectorAll('.main li')

          let tlq = gsap.timeline({ onComplete: done })

          tlq.to(el, { opacity: 0, x: '-5%', duration: 0.2, ease: 'power3.in' })
        }
      },
      leaveCancelled: function (el) {
        if (el.classList.contains('headerNav')) {
          const mainLi = el.querySelectorAll('.main li')

          gsap.set(el, { opacity: 0, x: '-5%' })
          gsap.set(mainLi, { opacity: 0, y: 20 })
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
        color: $lightgrey;
        font-family: '', sans-serif;
        text-transform: capitalize;
        font-family: 'Quicksand', sans-serif;
        font-weight: 700;
        font-size: 28px;
        opacity: 0.8;
        &.nuxt-link-exact-active,
        &:hover,
        &:active {
          color: $white;
          opacity: 1;
        }
        &.nuxt-link-exact-active {
          transform: translateX(20px);
          &::before {
            content: '';
            width: 3px;
            height: 26px;
            display: block;
            background: $white;
            position: absolute;
            top: 10px;
            left: -10px;
          }
        }
      }
    }
  }
</style>