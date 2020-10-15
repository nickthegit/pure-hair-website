<template>
  <section>
    <blockquote>
      <h3>
        "Words can be like X-rays, if you use them properly—they’ll go through
        anything. You read and you’re pierced."
      </h3>
      <cite>A name</cite>
    </blockquote>
  </section>
</template>

<script>
  export default {}
</script>

<style lang="scss" scoped>
  section {
    width: 100%;
    height: auto;
    background: $pink;
    blockquote {
      width: 100%;
      height: auto;
      max-width: $containerWidth;
      margin: 0 auto;
      position: relative;
      padding: 80px 40px;
    }
  }
</style>