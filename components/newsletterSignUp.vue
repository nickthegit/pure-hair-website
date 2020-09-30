<template>
  <aside>
    <article>
      <section class="img-wrap">
        <img src="~assets/placeholders/jon-tyson-XmMsdtiGSfo-unsplash.jpg" alt />
      </section>
      <section class="newsletter">
        <div class="newsletter__loading newsletter_section" v-if="status === 'requested'">Loading</div>
        <div class="newsletter__main-form newsletter_section">
          <h2>Get the latest offers & updates</h2>
          <h3>Subscribe to our Newsletter below.</h3>
          <form action>
            <input type="email" name id placeholder="Enter your email" />
            <button :disabled="status === 'requested'" type="submit">Subscribe</button>
          </form>
          <em v-show="error">{{ errorMsg }}</em>
        </div>
      </section>
    </article>
  </aside>
</template>

<script>
  export default {
    data() {
      return {
        userEmail: null,
        error: false,
        errorMsg: null,
        status: 'inactive', // inactive, requested, success, error
      }
    },
  }
</script>

<style lang="scss" scoped>
  aside {
    width: 100%;
    position: relative;
    overflow: hidden;
    padding: 20px;
    &::before {
      content: '';
      width: 200%;
      height: 200%;
      background: $pink;
      border-radius: 50%;
      display: block;
      position: absolute;
      top: 25%;
      right: -20%;
      z-index: -1;
    }
    article {
      width: 100%;
      height: auto;
      max-width: $mediumContainerWidth;
      margin: 20px auto;
      background: $white;
      display: grid;
      grid-template: auto / 45% 55%;
      border-radius: 80px;
      overflow: hidden;
      box-shadow: 0px 0px 24px 2px rgba($black, 0.075);
      @include breakpoint(tablet) {
        border-radius: 60px;
      }
      @include breakpoint(mobile) {
        border-radius: 50px;
        grid-template: auto auto / 100%;
      }
      // padding: 20px;
    }
    section {
      position: relative;
      width: 100%;
      height: 100%;
      &.newsletter {
      }
    }
    .img-wrap {
      width: 100%;
      height: 0;
      position: relative;
      padding-bottom: 100%;
    }
    img {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      object-fit: cover;
    }
    .newsletter {
      overflow: hidden;
      &_section {
        width: 100%;
        height: 100%;
        position: absolute;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 40px;
        padding-right: 80px;
        top: 0;
        left: 0;
      }
      &__loading {
        z-index: 2;
        text-align: center;
        background: rgba($white, 0.5);
        backdrop-filter: blur(2px);
      }
      &__main-form {
        z-index: 1;
        @include breakpoint(mobile) {
          padding: 30px;
        }
        h2 {
          font-family: 'Quicksand', sans-serif;
          font-weight: 700;
          font-size: 4vw;
          line-height: 90%;
          margin-bottom: 20px;
          color: $primary;
          @include breakpoint(mobile) {
            font-size: 8vw;
          }
        }
        h3 {
          font-family: 'EB Garamond', serif;
          font-weight: 400;
          font-size: 1.6vw;
          line-height: 110%;
          margin-bottom: 20px;
          color: $grey;
          @include breakpoint(mobile) {
            font-size: 6vw;
          }
        }
      }
    }
    form {
      width: 100%;
      input,
      button {
        width: 100%;
        border-radius: 10px;
        box-sizing: border-box;
        min-height: 40px;
        margin-bottom: 10px;
        text-align: center;
        padding: 15px 10px;
      }
      input {
        background: rgba($lightgrey, 0.2);
        border: 1px solid $lightgrey;
        font-size: 20px;
        color: $grey;
      }
      button {
        background: $black;
        color: $white;
        text-transform: uppercase;
        letter-spacing: 2px;
        border: none;
        cursor: pointer;
        &:hover,
        &:active {
          background: rgba($black, 0.8);
        }
      }
    }
    em {
      color: red;
    }
  }
</style>