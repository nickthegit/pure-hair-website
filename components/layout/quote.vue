<template>
  <section>
    <blockquote>
      <h3>"{{ quote }}"</h3>
      <cite>~ {{ cite }}</cite>
    </blockquote>
  </section>
</template>

<script>
  import { gsap } from 'gsap'
  import { ScrollTrigger } from 'gsap/ScrollTrigger'
  if (process.client) {
    gsap.registerPlugin(ScrollTrigger)
  }
  export default {
    props: {
      quote: {
        type: String,
        required: true,
      },
      cite: {
        type: String,
      },
    },
    mounted() {
      const quote = this.$el.querySelector('blockquote')
      gsap.from(quote, {
        duration: 1,
        y: 100,
        autoAlpha: 0,
        ease: 'back.out(1)',
        scrollTrigger: {
          trigger: quote,
          start: 'top bottom',
          end: '+=500',
          scrub: 1,
          // markers: true,
          // once: true,
        },
      })
    },
  }
</script>

<style lang="scss" scoped>
  section {
    width: 100%;
    height: auto;
    background: rgba($pink, 0.5);
  }
  blockquote {
    width: 100%;
    height: auto;
    max-width: $containerWidth;
    margin: 0 auto;
    position: relative;
    padding: 80px 40px;
    display: block;
  }
  cite {
    width: 100%;
    display: block;
    padding-top: 20px;
    text-align: right;
    font-size: 18px;
    text-transform: uppercase;
  }
</style>