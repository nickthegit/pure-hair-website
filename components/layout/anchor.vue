<template>
  <a :href="link" :class="type" target="_blank" rel="noopener noreferrer">
    <span>
      <slot />
    </span>
    <span>🔥🔥🔥</span>
  </a>
</template>

<script>
  export default {
    props: {
      link: {
        type: String,
        default: '/',
      },
      type: {
        type: String,
        default: 'primary', // alt
      },
    },
  }
</script>

<style lang="scss" scoped>
  a {
    width: auto;
    display: inline-block;
    color: $white;
    background: $primary;
    text-decoration: none;
    text-transform: uppercase;
    font-size: 16px;
    line-height: 16px;
    font-weight: 700;
    padding: 12px 25px 12px 25px;
    border-radius: 30px;
    text-align: center;
    position: relative;
    font-family: 'Quicksand', sans-serif;
    font-weight: 700;
    span {
      &:nth-child(2) {
        display: none;
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
      }
    }
    &.alt {
      color: $primary;
      background: $white;
      border: 2px solid $primary;
    }
    &:hover {
      span {
        &:nth-child(1) {
          // display: none;
          visibility: hidden;
        }
        &:nth-child(2) {
          display: inline-block;
        }
      }
    }
  }
</style>