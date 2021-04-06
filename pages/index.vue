<template>
  <main>
    <home-hero />
    <home-intro />
    <quote
      quote="Words can be like X-rays, if you use them properly—they’ll go through anything. You read and you’re pierced."
      cite="A name here"
    />
    <section id="homeLocations">
      <h2>Our Locations</h2>
      <article>
        <general-image imgSide="right" :imgPaths="imgPaths()" />
        <div>
          <h3>Sherborne</h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima,
            natus, sint quae animi optio fuga voluptatibus, similique autem
            deleniti ullam impedit in. Molestias beatae optio eligendi odio a
            cupiditate tempora!
          </p>
        </div>
      </article>
      <article>
        <general-image imgSide="right" :imgPaths="imgPaths()" />
        <div>
          <h3>Sturminster Newton</h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima,
            natus, sint quae animi optio fuga voluptatibus, similique autem
            deleniti ullam impedit in. Molestias beatae optio eligendi odio a
            cupiditate tempora!
          </p>
        </div>
      </article>
    </section>
  </main>
</template>

<script>
import Quote from '~/components/layout/quote.vue'
import homeHero from '~/components/pages/homeHero.vue'
import HomeIntro from '~/components/pages/homeIntro.vue'
import generalImage from '~/components/layout/generalImage.vue'
export default {
  components: { homeHero, HomeIntro, Quote, generalImage },
  mounted() {
    // * Access ENV with:
    // process.env.ENV_TEST
    // or
    // context.env.ENV_TEST
    // console.log(process.env.HOST_NAME)
  },
  methods: {
    imgPaths() {
      return {
        img480: `https://picsum.photos/400/300`,
        img600: `https://picsum.photos/400/300`,
        img800: `https://picsum.photos/400/300`,
        img960: `https://picsum.photos/400/300`,
        img1200: `https://picsum.photos/400/300`,
        img1400: `https://picsum.photos/400/300`,
        img1600: `https://picsum.photos/400/300`,
        img1800: `https://picsum.photos/400/300`,
        img2000: `https://picsum.photos/400/300`,
      }
    },
  },
}
</script>

<style lang="scss" scoped>
#homeLocations {
  width: 100%;
  height: auto;
  max-width: $containerWidth;
  margin: 0 auto;
  position: relative;
  padding: var(--global_padding);
  display: grid;
  grid-template: auto 10px auto / 1fr 1fr;
  column-gap: var(--global_padding);
  justify-items: start;
  align-items: top;
  padding-right: 0;
  @include breakpoint(mobile) {
    grid-template: auto auto auto / 100%;
    padding: var(--global_padding) 20px 0 20px;
  }
  h2 {
    grid-row: 1 / 3;
    grid-column: 1 / 4;
    position: relative;
    z-index: 10;
    padding-bottom: var(--global_padding);
    @include breakpoint(mobile) {
      grid-row: 1 / 2;
      grid-column: 1 / 2;
      padding-bottom: var(--global_padding);
    }
  }
  article {
    grid-row: 2 / 4;
    display: block;
    width: 100%;
    z-index: 1;
    position: relative;
    padding-bottom: var(--global_padding);
    h3 {
      margin-top: 20px;
    }
    p {
      margin-top: 20px;
    }
    p {
      color: $grey;
    }
    @include breakpoint(mobile) {
      grid-column: 1 / 2;
    }
    &:nth-child(2) {
      grid-column: 1 / 2;
      @include breakpoint(mobile) {
        grid-column: 1 / 2;
        grid-row: 2 / 3;
      }
    }
    &:last-child {
      grid-column: 2 / 3;
      @include breakpoint(mobile) {
        grid-column: 1 / 2;
        grid-row: 3 / 4;
      }
    }
    img {
      width: 100%;
    }
  }
}
</style>
