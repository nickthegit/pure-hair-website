<template>
  <section>
    <transition
      @before-enter="headline_beforeEnter"
      @enter="headline_enter"
      @leave="headline_leave"
      @enter-cancelled="headline_enterCancelled"
      @after-enter="headline_afterEnter"
      :css="false"
    >
      <div class="hero__headline-wrap" v-show="heroShow">
        <h1>
          <span>Step in.</span>
          <span>Sit.</span>
          <span>Relax.</span>
        </h1>
        <h2>We take care of everything & leave you feeling fabulous.</h2>
        <anchor link="dave" type="alt">Book an appointment</anchor>
      </div>
    </transition>
  </section>
</template>

<script>
  import { gsap } from 'gsap'
  import { ScrollTrigger } from 'gsap/ScrollTrigger'
  import { SplitText } from 'gsap/SplitText'

  // if (process.client) {
  gsap.registerPlugin(ScrollTrigger, SplitText)
  // }

  export default {
    data() {
      return {
        heroShow: false,
        heroFinished: false,
      }
    },
    computed: {
      headlineSpans: function () {
        return this.$el.querySelectorAll('h1 span')
      },
      wordDivs: function () {
        let mySplitText = new SplitText(this.$el.querySelectorAll('h2'), {
          type: 'words',
        })
        return mySplitText.words
      },
      ctaBtn: function () {
        return this.$el.querySelector('a')
      },
    },
    methods: {
      headline_beforeEnter: function (el) {
        gsap.set(this.headlineSpans, { autoAlpha: 0, y: 20 })
        gsap.set(this.wordDivs, { autoAlpha: 0, y: 5 })
        gsap.set(this.ctaBtn, { autoAlpha: 0, y: 10 })
      },
      headline_enter: function (el, done) {
        let vm = this
        let tl = gsap.timeline({
          onComplete: function () {
            vm.heroFinished = true
            done
          },
          delay: 0.2,
        })
        tl.to(
          this.headlineSpans,
          { autoAlpha: 1, y: 0, stagger: 0.25, duration: 0.5 },
          'tlStart'
        )
          .to(
            this.wordDivs,
            { autoAlpha: 1, y: 0, stagger: 0.05, duration: 0.1 },
            'tlStart+=0.9'
          )
          .to(this.ctaBtn, { autoAlpha: 1, y: 0, duration: 1 }, '-=0.0')
      },
      headline_afterEnter: function (el) {
        gsap.set(this.headlineSpans, { autoAlpha: 1, y: 0 })
        gsap.set(this.wordDivs, { autoAlpha: 1, y: 0 })
        gsap.set(this.ctaBtn, { autoAlpha: 1, y: 0 })
      },
      headline_enterCancelled: function (el) {
        gsap.set(this.headlineSpans, { autoAlpha: 1, y: 0 })
        gsap.set(this.wordDivs, { autoAlpha: 1, y: 0 })
        gsap.set(this.ctaBtn, { autoAlpha: 1, y: 0 })
      },
      headline_leave: function (el, done) {
        done()
      },
      headline_scroll_leave: function () {
        let outAnimationObj = {
          autoAlpha: 0,
          y: -20,
          duration: 1,
        }
        let tl = gsap.timeline({
          // yes, we can add it to an entire timeline!
          scrollTrigger: {
            trigger: this.$el,
            markers: false,
            pin: false, // pin the trigger element while active
            start: '10% top', // when the top of the trigger hits the top of the viewport
            end: '50% top', // end after scrolling 500px beyond the start
            scrub: 1, // smooth scrubbing, takes 1 second to "catch up" to the scrollbar
          },
        })
        tl.to(this.headlineSpans, {
          autoAlpha: 0,
          y: -20,
          stagger: 0.3,
          duration: 1,
        })
          .to(this.$el.querySelector('h2'), outAnimationObj)
          .to(this.ctaBtn, outAnimationObj)
      },
    },
    mounted() {
      this.$nextTick(() => {
        this.heroShow = true
        this.headline_scroll_leave()
      })
    },
    head() {
      return {
        htmlAttrs: {
          class: !this.heroFinished ? 'noScroll' : '',
        },
      }
    },
  }
</script>

<style lang="scss" scoped>
  section {
    width: 100%;
    min-height: 100vh;
    max-width: $containerWidth;
    margin: 0 auto;
    position: relative;
    top: 0;
    left: 0;
    padding: 40px;
    display: grid;
    grid-template: 100% / 40% 10% 50%;
    justify-items: start;
    align-items: center;
    @include breakpoint(tablet-mobile) {
      padding-top: 80px;
      grid-template: auto 1fr / 100%;
    }
    @include breakpoint(mobile) {
      padding: 80px 20px 40px 20px;
    }
  }
  .hero__headline-wrap {
    grid-column: 1 / 3;
  }
  h1 {
    font-size: 8vw;
    line-height: 90%;
    color: $primary;
    span {
      display: block;
    }
    @include breakpoint(tablet) {
      font-size: 15vw;
    }
    @include breakpoint(mobile) {
      font-size: 20vw;
    }
  }
  h2 {
    margin: 20px 0;
    font-size: 2.2vw;
    line-height: 110%;
    font-family: 'EB Garamond', serif;
    font-weight: 400;
    color: $grey;
    @include breakpoint(tablet) {
      font-size: 5vw;
    }
    @include breakpoint(mobile) {
      font-size: 6vw;
    }
  }
</style>