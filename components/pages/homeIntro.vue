<template>
  <section>
    <div class="text-wrap section-item__1">
      <h2>finest salon experience in Sherborne, Dorset.</h2>
      <p>
        It is our mission at PURE HAIR to provide our clients with the highest
        degree of customer service in a professional comfortable setting.
      </p>
    </div>
    <general-image class="section-item__2" :imgRatio="[3, 2]" />
    <general-image class="section-item__3" />
    <general-image class="section-item__4" />
    <general-image class="section-item__5" />
    <div class="text-wrap section-item__6">
      <p>
        At PURE HAIR we strive for every guest to feel cared for and beautiful.
        We promise to always provide an open and welcoming environment, while
        performing the highest level of service.
      </p>
      <p>
        what makes us different at Pure Hair? We are committed to progress.
        Through continuous education and development of our team. Our team is
        extremely talented, honest and passionate. We are committed to
        performing our crafts exceptionally well and continually strive to
        improve ourselves
      </p>
    </div>
    <div class="text-wrap section-item__7">
      <h2>
        Through education, dedication and skill, we pledge to create a culture
        of love, positivity and satisfaction for our clients every time.
      </h2>
    </div>
    <div class="text-wrap section-item__8">
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
      <p>
        Whether it’s subtly evolving, maintaining or totally transforming your
        hair, PUREHAIR’s team of STYLISTS are committed to caring for the health
        of your hair at every stage. Creating lasting relationships with our
        clients is extremely important to us at Pure Hair.
      </p>
    </div>
    <general-image class="section-item__9" />
    <general-image class="section-item__10" />
  </section>
</template>

<script>
  export default {}
</script>

<style lang="scss" scoped>
  section {
    width: 100%;
    height: auto;
    max-width: $containerWidth;
    margin: 0 auto;
    position: relative;
    padding: 40px;
    display: grid;
    grid-template: auto / repeat(5, calc(20% - (40px * 4 / 5)));
    column-gap: 40px;
    row-gap: 20px;
    justify-items: start;
    align-items: center;
    @include breakpoint(mobile) {
      padding: 20px;
    }
  }
  .text-wrap {
    margin: 40px 0;
    display: block;
    @include breakpoint(mobile) {
      margin: 20px 0;
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
      grid-column: 1 / 4;
      grid-row: span 3;
      @include breakpoint(mobile) {
        grid-column: 1 / 6;
      }
    }
    &__2 {
      grid-column: 4 / 5;
      @include breakpoint(mobile) {
        grid-column: 1 / 4;
      }
    }
    &__3 {
      grid-column: 4 / 6;
      @include breakpoint(mobile) {
        grid-column: 1 / 6;
      }
    }
    &__4 {
      grid-column: 5 / 6;
      @include breakpoint(mobile) {
        grid-column: 3 / 6;
      }
    }
    &__5 {
      grid-column: 1 / 4;
      @include breakpoint(mobile) {
        grid-column: 1 / 6;
      }
    }
    &__6 {
      grid-column: 4 / 6;
      @include breakpoint(mobile) {
        grid-column: 1 / 6;
      }
    }
    &__7 {
      grid-column: 1 / 6;
    }
    &__8 {
      grid-column: 1 / 4;
      grid-row: span 2;
      @include breakpoint(mobile) {
        grid-column: 1 / 6;
      }
    }
    &__9 {
      grid-column: 4 / 6;
      @include breakpoint(mobile) {
        grid-column: 1 / 6;
      }
    }
    &__10 {
      grid-column: 4 / 6;
      @include breakpoint(mobile) {
        grid-column: 1 / 6;
      }
    }
  }
</style>