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
      <article>Sherbz</article>
      <article>Sturminster</article>
    </section>
  </main>
</template>

<script>
  export default {
    mounted() {
      // * Access ENV with:
      // process.env.ENV_TEST
      // or
      // context.env.ENV_TEST
      // console.log(process.env.HOST_NAME)
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
    padding: 40px;
    display: grid;
    grid-template: auto 200px auto / 50% 50%;
    column-gap: 40px;
    row-gap: 20px;
    justify-items: start;
    align-items: center;
    @include breakpoint(mobile) {
      padding: 20px;
    }
  }
</style>
