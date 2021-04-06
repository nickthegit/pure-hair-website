<template>
  <aside>
    <article>
      <section class="img-wrap">
        <img
          src="~assets/placeholders/jon-tyson-XmMsdtiGSfo-unsplash.jpg"
          alt
        />
      </section>
      <mc-newsletter />
    </article>
  </aside>
</template>

<script>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import McNewsletter from './mcNewsletter.vue'

gsap.registerPlugin(ScrollTrigger)

export default {
  components: {
    McNewsletter,
  },
  mounted() {
    let tl = gsap.timeline({
      scrollTrigger: {
        trigger: this.$el,
        markers: false,
        pin: false, // pin the trigger element while active
        start: '20% bottom', // when the top of the trigger hits the top of the viewport
        end: '90% bottom', // end after scrolling 500px beyond the start
        scrub: 1, // smooth scrubbing, takes 1 second to "catch up" to the scrollbar
      },
    })
    tl.fromTo(
      this.$el.querySelector('article'),
      {
        autoAlpha: 0,
        y: 120,
      },
      {
        autoAlpha: 1,
        y: 0,
        duration: 1,
      },
      'start'
    ).fromTo(
      this.$el.querySelector('img'),
      {
        autoAlpha: 0,
        y: 80,
      },
      {
        autoAlpha: 1,
        y: 0,
        duration: 0.5,
      },
      'start'
    )
  },
}
</script>

<style lang="scss" scoped>
aside {
  width: 100%;
  position: relative;
  overflow: hidden;
  padding: 20px;
  &::before {
    content: '';
    width: 200%;
    height: 200%;
    background: $pink;
    border-radius: 50%;
    display: block;
    position: absolute;
    top: 25%;
    right: -20%;
    z-index: -1;
  }
  article {
    width: 100%;
    height: auto;
    max-width: $mediumContainerWidth;
    margin: 20px auto;
    background: $white;
    display: grid;
    grid-template: auto / 45% 55%;
    border-radius: 80px;
    overflow: hidden;
    box-shadow: 0px 0px 24px 2px rgba($black, 0.075);
    @include breakpoint(tablet) {
      border-radius: 60px;
    }
    @include breakpoint(mobile) {
      border-radius: 50px;
      grid-template: auto auto / 100%;
    }
    // padding: 20px;
  }
  section {
    position: relative;
    width: 100%;
    height: 100%;
  }
  .img-wrap {
    width: 100%;
    height: 0;
    position: relative;
    padding-bottom: 100%;
  }
  img {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    object-fit: cover;
  }
}
</style>
