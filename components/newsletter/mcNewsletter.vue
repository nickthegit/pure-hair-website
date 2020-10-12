<template>
  <mailchimp-subscribe
    url="https://purehairsherborne.us16.list-manage.com/subscribe/post-json"
    user-id="bf3efe90016bb9625a276a625"
    list-id="05a426e48e"
    @error="onError"
    @success="onSuccess"
  >
    <template v-slot="{ subscribe, setEmail, error, success, loading }">
      <section class="newsletter">
        <transition
          @before-enter="successBeforeEnter"
          @enter="successEnter"
          @leave="successLeave"
          @leave-cancelled="successLeaveCancelled"
          :css="false"
        >
          <div v-if="success" class="newsletter__success newsletter_section">
            <h2>Thanks!</h2>
            <h3>
              You are now subscribed to our newsletter. Keep a check of your
              inbox for the latest updates and offers.
            </h3>
          </div>
        </transition>
        <transition
          @before-enter="loadingBeforeEnter"
          @enter="loadingEnter"
          @leave="loadingLeave"
          @leave-cancelled="loadingLeaveCancelled"
          :css="false"
        >
          <div
            v-if="loading"
            class="newsletter__loading newsletter_section"
          ></div>
        </transition>
        <div class="newsletter__main-form newsletter_section">
          <h2>Get the latest offers & updates</h2>
          <h3>Subscribe to our Newsletter below.</h3>
          <form @submit.prevent="subscribe">
            <input
              type="email"
              placeholder="Enter your email"
              @input="setEmail($event.target.value)"
            />
            <button type="submit">Subscribe</button>
          </form>
          <em v-show="error" v-html="error"></em>
        </div>
      </section>
    </template>
  </mailchimp-subscribe>
</template>

<script>
  import MailchimpSubscribe from 'vue-mailchimp-subscribe'
  import { gsap } from 'gsap'
  export default {
    components: {
      MailchimpSubscribe,
    },
    data() {
      return {}
    },
    methods: {
      onError(err) {
        // handle error
        console.log('err', err)
      },
      onSuccess() {
        const vm = this
        setTimeout(() => {
          vm.$children[0].success = false
        }, 4000)
      },
      loadingBeforeEnter() {
        gsap.set(this.$el.querySelector('.newsletter__loading'), { autoAlpha: 0 })
      },
      loadingEnter() {
        gsap.fromTo(
          this.$el.querySelector('.newsletter__loading'),
          { autoAlpha: 0 },
          { autoAlpha: 1, duration: 0.2 }
        )
      },
      loadingLeave() {
        gsap.to(this.$el.querySelector('.newsletter__loading'), {
          autoAlpha: 0,
          duration: 0.1,
        })
      },
      loadingLeaveCancelled() {
        gsap.set(this.$el.querySelector('.newsletter__loading'), { autoAlpha: 0 })
      },
      successBeforeEnter() {
        gsap.set(this.$el.querySelector('.newsletter__success'), { autoAlpha: 0 })
        gsap.set(this.$el.querySelector('.newsletter__success'), { autoAlpha: 0 })
      },
      successEnter() {
        gsap.fromTo(
          this.$el.querySelector('.newsletter__success'),
          { autoAlpha: 0 },
          { autoAlpha: 1, duration: 0.3 }
        )
      },
      successLeave() {
        gsap.to(this.$el.querySelector('.newsletter__success'), {
          autoAlpha: 0,
          duration: 0.3,
        })
      },
      successLeaveCancelled() {
        gsap.set(this.$el.querySelector('.newsletter__success'), { autoAlpha: 0 })
      },
    },
    mounted() {
      // console.log(this)
    },
  }
</script>

<style lang="scss" scoped>
  section {
    position: relative;
    width: 100%;
    height: 100%;
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
      @include breakpoint(mobile) {
        padding: 30px;
        position: relative;
      }
      h2 {
        font-family: 'Quicksand', sans-serif;
        font-weight: 700;
        font-size: 45px;
        font-size: clamp(30px, 4vw, 55px);
        line-height: 90%;
        margin-bottom: 20px;
        color: $primary;
      }
      h3 {
        font-family: 'EB Garamond', serif;
        font-weight: 400;
        font-size: 1.6vw;
        font-size: clamp(20px, 1.8vw, 28px);
        line-height: 110%;
        margin-bottom: 20px;
        color: $grey;
      }
    }
    &__loading {
      z-index: 2;
      text-align: center;
      background: rgba($white, 0.5);
      backdrop-filter: blur(2px);
    }
    &__success {
      z-index: 2;
      text-align: center;
      background: rgba($white, 0.9);
      backdrop-filter: blur(2px);
    }
    &__main-form {
      z-index: 1;
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
</style>