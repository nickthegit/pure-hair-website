<template>
  <section class="home_hero">
    <div class="hero__headline-wrap" v-show="heroShow">
      <h1>
        <span>Step in.</span>
        <span>Sit.</span>
        <span>Relax.</span>
      </h1>
      <h2>We take care of everything & leave you feeling fabulous.</h2>
      <anchor link="/" type="alt">Book an appointment</anchor>
    </div>
    <div class="hero__background-fill"></div>
    <div class="hero__pattern"></div>
    <div class="hero__img-wrap">
      <general-image
        :imgPaths="imgPaths"
        imgAlt="Pure Hair hero image"
        :imgRatio="$device.isMobile ? [2, 2] : [3, 2]"
      />
    </div>
  </section>
</template>

<script>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import anchor from '../layout/anchor.vue'
import GeneralImage from '../layout/generalImage.vue'
if (process.client) {
  gsap.registerPlugin(ScrollTrigger)
}
// define repeatable els
let vm,
  el,
  headlineSpans,
  subtitle,
  ctaBtn,
  picture,
  background,
  pattern,
  imgWrap,
  img

export default {
  components: { anchor, GeneralImage },
  data() {
    return {
      heroShow: false,
      heroFinished: false,
      imgPaths: {
        img480:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_480/v1617742649/purehair/hero-image.jpg',
        img600:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_600/v1617742649/purehair/hero-image.jpg',
        img800:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_800/v1617742649/purehair/hero-image.jpg',
        img960:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_960/v1617742649/purehair/hero-image.jpg',
        img1200:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_1200/v1617742649/purehair/hero-image.jpg',
        img1400:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_1400/v1617742649/purehair/hero-image.jpg',
        img1600:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_1600/v1617742649/purehair/hero-image.jpg',
        img1800:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_1800/v1617742649/purehair/hero-image.jpg',
        img2000:
          'https://res.cloudinary.com/nickjohn/image/upload/c_scale,f_auto,q_auto,w_2000/v1617742649/purehair/hero-image.jpg',
      },
    }
  },
  computed: {},
  methods: {
    vars() {
      // * vars
      ;(vm = this),
        (el = this.$el),
        (headlineSpans = this.$el.querySelectorAll('h1 span')),
        (subtitle = this.$el.querySelectorAll('h2')),
        (ctaBtn = this.$el.querySelector('a')),
        (picture = this.$el.querySelector('picture')),
        (background = this.$el.querySelector('.hero__background-fill')),
        (pattern = this.$el.querySelector('.hero__pattern')),
        (imgWrap = this.$el.querySelector('.hero__img-wrap')),
        (img = this.$el.querySelector('img'))
    },
    sets() {
      // * sets
      gsap.set(headlineSpans, { autoAlpha: 0, y: 20 })
      gsap.set(subtitle, { autoAlpha: 0, y: 5 })
      gsap.set(ctaBtn, { autoAlpha: 0, y: 10 })
      gsap.set(imgWrap, { autoAlpha: 0, y: 20 })
      gsap.set(background, { autoAlpha: 0, x: 70 })
      gsap.set(pattern, { autoAlpha: 0, x: 70 })
    },
    enterAnimation() {
      this.sets()
      // * enter tl
      let tl = gsap.timeline({
        onComplete: function () {
          vm.heroFinished = true
        },
        delay: 0.2,
      })
      tl.to(
        headlineSpans,
        { autoAlpha: 1, y: 0, stagger: 0.25, duration: 0.5 },
        'tlStart'
      )
        .to(subtitle, { autoAlpha: 1, y: 0, duration: 0.2 }, 'tlStart+=0.9')
        .to(ctaBtn, { autoAlpha: 1, y: 0, duration: 0.5 }, '-=0.1')
        .to(background, { autoAlpha: 0.075, x: 0, duration: 0.75 }, '-=0.5')
        .to(pattern, { autoAlpha: 0.4, x: 0, duration: 0.75 }, '-=0.1')
        .to(imgWrap, { autoAlpha: 1, y: 0, duration: 2 }, '-=1.2')
    },
    hero_scroll_leave() {
      // * define tl's
      let tl = gsap.timeline({
        // yes, we can add it to an entire timeline!
        scrollTrigger: {
          trigger: el,
          markers: true,
          pin: false, // pin the trigger element while active
          start: 'top top', // when the top of the trigger hits the top of the viewport
          end: '50% top', // end after scrolling 500px beyond the start
          scrub: 1, // smooth scrubbing, takes 1 second to "catch up" to the scrollbar
        },
      })
      tl.to(
        headlineSpans,
        {
          autoAlpha: 0,
          y: -20,
          stagger: 0.3,
          duration: 1,
        },
        'start'
      )
      //   .to(subtitle, { autoAlpha: 0, y: -20, duration: 1 })
      //   .to(ctaBtn, { autoAlpha: 0, y: -20, duration: 1 })
      //   .to(pattern, { autoAlpha: 0, x: 70, duration: 1 }, '-=0.5')
      //   .to(background, { autoAlpha: 0, x: '100%', duration: 2 }, 'start+=0.1')
      //   .to(
      //     img,
      //     {
      //       scrollTrigger: {
      //         trigger: img,
      //         markers: true,
      //         pin: false,
      //         start: '20% top',
      //         end: '100% top',
      //         scrub: 1,
      //       },
      //       y: '15%',
      //       autoAlpha: 0,
      //       duration: 0.3,
      //       ease: 'none',
      //     },
      //     'img-pin'
      //   )

      // masterTl.add(headlineTl, 'start')
      // .add(imgTl, 'start')
    },
  },
  async mounted() {
    await this.vars()
    await this.enterAnimation()
    this.$nextTick(async () => {
      this.heroShow = await true
      // await this.hero_scroll_leave()
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
  padding: 0 0 0 40px;
  display: grid;
  grid-template: 100% / 40% 10% 50%;
  justify-content: start;
  align-items: center;
  overflow-x: hidden;
  @include breakpoint(tablet-mobile) {
    padding: 80px 0 0 0;
    grid-template: 7% auto 7% 5% auto / 100%;
    height: auto;
    justify-content: center;
    align-items: start;
  }
  @include breakpoint(tablet) {
    grid-template: 7% auto 10% 30px auto / 100%;
  }
  @include breakpoint(mobile) {
    padding: 60px 0 0 0;
  }
}
.hero {
  &__headline-wrap {
    grid-column: 1 / 2;
    position: relative;
    z-index: 3;
    padding-right: 40px;
    width: 100%;
    @include breakpoint(tablet-mobile) {
      padding: 20px;
      grid-row: 5 / 6;
    }
    h1 {
      font-size: 100px;
      font-size: clamp(75px, 7.2vw, 150px);
      line-height: 85%;
      color: $primary;
      span {
        display: block;
      }
    }
    h2 {
      margin: 20px 0;
      font-size: 40px;
      font-size: clamp(30px, 2.2vw, 50px);
      line-height: 110%;
      font-family: 'EB Garamond', serif;
      font-weight: 400;
      color: $grey;
    }
  }
  &__background-fill {
    grid-column: 3 / 4;
    width: 100%;
    height: 100%;
    position: absolute;
    background: $primary;
    z-index: 1;
    opacity: 0.075;
    @include breakpoint(tablet-mobile) {
      grid-column: 1 / 2;
      grid-row: 2 / 4;
    }
  }
  &__pattern {
    width: 90%;
    grid-column: 2 / 4;
    height: 40%;
    background-image: url('~assets/img/patterns/bank-note.svg');
    background-repeat: repeat;
    background-size: 24%;
    position: absolute;
    z-index: 2;
    bottom: 10%;
    right: 0;
    opacity: 0.4;
    @include breakpoint(tablet-mobile) {
      grid-column: 1 / 2;
      grid-row: 1 / 5;
      bottom: 2%;
      height: 40%;
      right: unset;
      left: 0;
    }
  }
  &__img-wrap {
    grid-column: 2 / 4;
    width: 100%;
    height: auto;
    position: absolute;
    z-index: 2;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-right: 40px;
    picture {
      padding-bottom: (33 / 50) * 100%;
    }
    @include breakpoint(tablet-mobile) {
      grid-column: 1 / 2;
      grid-row: 1 / 3;
      height: auto;
      position: relative;
      padding: 20px;
      box-sizing: border-box;
    }
    @include breakpoint(mobile) {
      picture {
        padding-bottom: 100%;
      }
    }
  }
}
</style>
