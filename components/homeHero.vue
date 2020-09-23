<template>
  <section>
    <div class="hero__headline-wrap">
      <h1>
        <span>Step in.</span>
        <span>Sit.</span>
        <span>Relax.</span>
      </h1>
      <h2>We take care of everything & leave you feeling fabulous</h2>
      <anchor link="dave" type="alt">Book an appointment</anchor>
    </div>
  </section>
</template>

<script>
  export default {}
</script>

<style lang="scss" scoped>
  section {
    width: 100%;
    min-height: 100vh;
    // background: chocolate;
    position: relative;
    top: 0;
    left: 0;
    padding: (40px + $headerHeight) 40px 40px 40px;
    display: grid;
    grid-template: 100% / 40% 10% 50%;
    justify-items: start;
    align-items: center;
    @include breakpoint(tablet-mobile) {
      grid-template: auto 1fr / 100%;
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
    font-family: 'Kumbh Sans', sans-serif;
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