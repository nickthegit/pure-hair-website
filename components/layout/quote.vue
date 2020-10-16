<template>
  <section>
    <blockquote>
      <h3>"{{ quote }}"</h3>
      <cite>~ {{ cite }}</cite>
    </blockquote>
  </section>
</template>

<script>
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
  }
</script>

<style lang="scss" scoped>
  section {
    width: 100%;
    height: auto;
    background: $pink;
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