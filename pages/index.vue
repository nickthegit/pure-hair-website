<template>
  <main>
    <home-hero />
    <home-intro />
    <quote
      quote="Words can be like X-rays, if you use them properly—they’ll go through anything. You read and you’re pierced."
      cite="A name here"
    />
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
</style>
