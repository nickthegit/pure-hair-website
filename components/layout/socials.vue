<template>
  <ul :class="uid">
    <li>
      <a
        href="http://facebook.com"
        target="_blank"
        rel="noopener noreferrer"
        :class="['social-icon', facebook.slug]"
        v-html="facebook.svg"
      ></a>
    </li>
    <li>
      <a
        href="http://twitter.com"
        target="_blank"
        rel="noopener noreferrer"
        :class="['social-icon', twitter.slug]"
        v-html="twitter.svg"
      ></a>
    </li>
    <li>
      <a
        href="http://instagram.com"
        target="_blank"
        rel="noopener noreferrer"
        :class="['social-icon', instagram.slug]"
        v-html="instagram.svg"
      ></a>
    </li>
  </ul>
</template>

<script>
  const facebook = require('simple-icons/icons/facebook')
  const twitter = require('simple-icons/icons/twitter')
  const instagram = require('simple-icons/icons/instagram')
  // const linkedin = require('simple-icons/icons/linkedin')
  // const spotify = require('simple-icons/icons/spotify')
  // const vimeo = require('simple-icons/icons/vimeo')
  // const youtube = require('simple-icons/icons/youtube')

  // facebook.hex

  // console.log(spotify, linkedin, instagram, twitter, facebook, youtube, vimeo)
  export default {
    props: {
      uid: {
        type: String,
      },
    },
    data: () => {
      return {
        facebook,
        twitter,
        instagram,
        // linkedin,
        // spotify,
        // vimeo,
        // youtube,
      }
    },
    mounted() {
      // console.log(this.spotify.svg)
    },
  }
</script>

<style lang="scss">
  .headerSocials {
    padding: 0px 20px 20px 40px;
    li {
      display: inline-block;
    }
    a {
      display: block;
      width: 50px;
      height: 30px;
      padding: 0 10px;
    }
    svg {
      display: block;
      width: 100%;
      height: auto;
      fill: $white;
    }
  }
</style>