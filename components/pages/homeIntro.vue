<template>
  <article>
    <general-image class="section-item__3" :imgPaths="imgPaths(4)" />
    <section class="text-wrap section-item__1">
      <h2>The finest salon experience in Dorset.</h2>
      <p>
        It is our mission at PURE HAIR to provide our clients with the highest
        degree of customer service in a professional comfortable setting.
      </p>
      <p>
        At PURE HAIR we strive for every guest to feel cared for and beautiful.
        We promise to always provide an open and welcoming environment, while
        performing the highest level of service.
      </p>
      <!-- <p>
        what makes us different at Pure Hair? We are committed to progress.
        Through continuous education and development of our team. Our team is
        extremely talented, honest and passionate. We are committed to
        performing our crafts exceptionally well and continually strive to
        improve ourselves
      </p> -->
    </section>
    <section class="text-wrap section-item__7">
      <h2>
        Through education, dedication and skill, we pledge to create a culture
        of love, positivity and satisfaction for our clients every time.
      </h2>
    </section>
    <section class="text-wrap section-item__6">
      <h2>A true listener hears more than just words.</h2>
      <p>
        At PURE HAIR, we believe understanding your personal image and style is
        a huge factor in determining a bespoke technique to create a final look
        most suited to you.
      </p>
      <p>
        Personalised consultations and made-to-measure colour services are
        designed to create a look suited to your natural complexion, eye colour
        and fashion style.
      </p>
      <!-- <p>
        Whether it’s subtly evolving, maintaining or totally transforming your
        hair, PUREHAIR’s team of STYLISTS are committed to caring for the health
        of your hair at every stage. Creating lasting relationships with our
        clients is extremely important to us at Pure Hair.
      </p> -->
    </section>
    <general-image
      class="section-item__5"
      imgSide="left"
      :imgPaths="imgPaths(3)"
    />
  </article>
</template>

<script>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import generalImage from '../layout/generalImage.vue'
if (process.client) {
  gsap.registerPlugin(ScrollTrigger)
}
export default {
  components: { generalImage },
  mounted() {
    const textBoxes = this.$el.querySelectorAll('.text-wrap')
    textBoxes.forEach((textBox) => {
      gsap.from(textBox, {
        duration: 1,
        y: 100,
        autoAlpha: 0,
        ease: 'back.out(1)',
        scrollTrigger: {
          trigger: textBox,
          start: 'top bottom',
          end: '+=500',
          scrub: 1,
          // markers: true,
          // once: true,
        },
      })
    })
  },
  methods: {
    imgPaths(num) {
      return {
        img480: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img600: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img800: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img960: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img1200: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img1400: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img1600: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img1800: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
        img2000: `/selects/photo-2020${num ? '-' + num : ''}.jpg`,
      }
    },
  },
}
</script>

<style lang="scss" scoped>
article {
  width: 100%;
  height: auto;
  max-width: $containerWidth;
  margin: 0 auto;
  position: relative;
  padding: var(--global_padding);
  display: grid;
  grid-template: auto / repeat(
      6,
      calc(16.666666% - (var(--global_padding) * 5 / 6))
    );
  column-gap: var(--global_padding);
  row-gap: var(--global_padding);
  justify-items: start;
  align-items: center;
}
.text-wrap {
  margin: 40px 0;
  display: block;
  @include breakpoint(mobile) {
    margin: 20px 0;
  }
  h2 {
    text-transform: capitalize;
  }
  h2,
  p {
    margin-bottom: 20px;
  }
  p {
    color: $grey;
  }
}
.section-item {
  &__1 {
    grid-column: 4 / 7;
    @include breakpoint(mobile) {
      grid-column: 1 / 7;
    }
  }
  // &__2 {
  //   grid-column: 5 / 6;
  //   @include breakpoint(mobile) {
  //     grid-column: 1 / 4;
  //   }
  // }
  &__3 {
    grid-column: 1 / 4;
    @include breakpoint(mobile) {
      grid-column: 1 / 7;
    }
  }
  // &__4 {
  //   grid-column: 6 / 7;
  //   @include breakpoint(mobile) {
  //     grid-column: 3 / 6;
  //   }
  // }
  &__5 {
    grid-column: 4 / 7;
    @include breakpoint(mobile) {
      grid-column: 1 / 7;
    }
  }
  &__6 {
    grid-column: 1 / 4;
    @include breakpoint(mobile) {
      grid-column: 1 / 7;
    }
  }
  &__7 {
    grid-column: 1 / 7;
  }
}
</style>
