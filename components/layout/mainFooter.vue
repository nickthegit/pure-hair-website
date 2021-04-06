<template>
  <footer>
    <div class="footer-main">
      <section class="footer-main__brand-section">
        <nuxt-link to="/">
          <logo-2 />
        </nuxt-link>
      </section>
      <section class="footer-main__main-nav">
        <nav>
          <ul>
            <li>
              <nuxt-link to="/">Home</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/fdsf">Our Story</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/dfd">Services</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/a-page">Prices</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/dfd">Stylists</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/a-page">Contact</nuxt-link>
            </li>
            <li>
              <a href="http://" target="_blank" rel="noopener noreferrer"
                >Book Online</a
              >
            </li>
          </ul>
        </nav>
      </section>
      <section class="footer-main__main-nav">
        <secondary-nav />
      </section>
      <section class="footer-main__contact">
        <address>
          <ul>
            <li>
              Pure Hair,
              <br />Half Moon St, <br />Sherborne, <br />DT9 3LN
            </li>
            <li>
              <a href="tel:+44 1935 814172" rel="noopener noreferrer"
                >01935 814172</a
              >
            </li>
            <li>
              <a
                href="mailto:hello@pure-hair.co.uk"
                target="_blank"
                rel="noopener noreferrer"
                >hello@pure-hair.co.uk</a
              >
            </li>
          </ul>
        </address>
      </section>
    </div>
    <section class="footer-bottom-bar">
      <div>
        <p>© Pure Hair {{ year }}, All rights reserved.</p>
        <socials />
      </div>
    </section>
  </footer>
</template>

<script>
import logo2 from '../logos/logo2.vue'
import SecondaryNav from './secondaryNav.vue'
import Socials from './socials.vue'
export default {
  components: { logo2, SecondaryNav, Socials },
  computed: {
    year() {
      return new Date().getFullYear()
    },
  },
}
</script>

<style lang="scss">
footer {
  width: 100%;
  height: auto;
  background: $darkgrey;
  background: linear-gradient(
    180deg,
    rgba(51, 55, 71, 1) 0%,
    rgba(35, 38, 48, 1) 100%
  );
  color: $lightgrey;
}
.footer-main {
  width: 100%;
  max-width: $mediumContainerWidth;
  margin: 0 auto;
  display: grid;
  grid-template: auto / 25% 25% 25% 25%;
  @include breakpoint(mobile) {
    grid-template: auto / 100%;
  }
  li {
    margin-bottom: 10px;
  }
  section {
    position: relative;
    width: 100%;
    padding: 40px 20px;
    display: flex;
    text-align: right;
    align-items: flex-start;
    justify-content: flex-end;
    font-size: 14px;
    line-height: 130%;
    @include breakpoint(mobile) {
      padding-bottom: 0;
    }
    a {
      color: $lightgrey;
      text-decoration: none;
      display: block;
      &.nuxt-link-exact-active,
      &:hover,
      &:active {
        color: $white;
        text-decoration: underline;
      }
    }
  }
  &__brand-section {
    justify-content: flex-start !important;
    a {
      display: block;
      width: 50%;
      max-width: 150px;
    }
    svg {
      fill: $lightgrey;
      width: 100%;
      height: auto;
    }
  }
}
.footer-bottom-bar {
  width: 100%;
  background: $black;
  @include breakpoint(mobile) {
    margin-top: 20px;
  }
  div {
    width: 100%;
    max-width: $mediumContainerWidth;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 20px;
  }
  p {
    font-size: 12px;
    color: $grey;
  }
  ul {
    height: auto;
  }
  li {
    display: inline-block;
  }
  a {
    display: inline-block;
    width: 25px;
    margin-left: 10px;
    @include breakpoint(mobile) {
      width: 20px;
      margin-left: 5px;
    }
    &:hover {
      svg {
        fill: $white;
      }
    }
    // height: 30px;
  }
  svg {
    display: block;
    width: 100%;
    height: auto;
    fill: $grey;
  }
}
</style>
