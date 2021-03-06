<template>
  <section class="nModes">
    <div class="container">
      <h2 class="nModes_Title"><span>Rendering modes</span></h2>
      <div class="row">
        <ul class="nModes_Tabs">
          <li class="nModes_Tabs_Option" :class="{'nModes_Tabs_Option--selected-first': mode === 0}" @click="mode = 0">Server Side Rendered</li>
          <li class="nModes_Tabs_Option" :class="{'nModes_Tabs_Option--selected': mode === 1}" @click="mode = 1">Statically Generated</li>
          <li class="nModes_Tabs_Option" :class="{'nModes_Tabs_Option--selected-last': mode === 2}" @click="mode = 2">Single Page App</li>
        </ul>
        <div class="nModes_Content">
          <div v-show="mode === 0">
            <h3 class="nModes_Content_Title">Server Side Rendered (Universal)</h3>
            <p class="nModes_Content_Description">
              The most popular mode for Nuxt. With SSR, also called "universal" or "isomorphic" mode, a Node.js server
              will be used to deliver HTML based on your Vue components to the client instead of the pure javascript.
              Using SSR will lead to a large SEO boost, better UX and more opportunities (compared to a traditional Vue SPA).
              <br><br>
              Because implementing SSR on your own can be really tedious, Nuxt.js gives you full support out of the box
              and will take care of common pitfalls.
            </p>
          </div>
          <div v-show="mode === 1">
            <h3 class="nModes_Content_Title">Statically Generated (Pre-Rendering)</h3>
            <p class="nModes_Content_Description">
              Static Site Generation is a very hot topic right now! Instead of switching to another framework and
              spending time to get used to it, why not killing two birds with one stone?
              <span style="color: #777">(only proverbial 🐦🐦)</span><br><br>
              Nuxt.js supports generating a static website based on your Vue application. It is the "best of both worlds"
              as you don't need a server but still have SEO benefits because Nuxt will pre-render all pages and include
              the necessary HTML. Also, you can deploy the resulting page easily to Netlify or GitHub pages.
            </p>
          </div>
          <div v-show="mode === 2">
            <h3 class="nModes_Content_Title">Single Page Application (SPA)</h3>
            <p class="nModes_Content_Description">
              Don't need SSR or Static Site Generation but still want to profit from the benefits that Nuxt provides?
              Are you slowly transitioning your app and want to start lightweight? Then the traditional SPA mode will
              likely be your choice.
              The outcome will be a typical Vue SPA as you know it but influenced by your Nuxt configuration and the
              framework itself.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      mode: 0
    }
  }
}
</script>

<style lang="scss">
.nModes {
  z-index: 100;
  position: relative;
  box-shadow: $--box-shadow-1;
  padding: 5rem 1rem;
  @media (min-width: $--md) {
    padding: 8rem 0;
  }
  &_Title {
    text-align: center;
    margin-top: 0;
    color: $color-text-primary;
    font-size: $h2-font-size;
    font-weight: $font-weight-regular;
    line-height: normal;
    margin-bottom: 6rem;
    span {
      padding-bottom: 10px;
      border-bottom: 4px solid $color-vue-green;
      border-radius: 4px;
    }
  }
  &_Tabs {
    width: 100%;
    padding: 0;
    list-style: none;
    @media (min-width: $--md) {
      width: 30%;
    }
    &_Option {
      position: relative;
      color: $color-text-regular;
      cursor: pointer;
      padding: 10px 0;
      font-size: $font-size-lg;
      font-weight: $font-weight-light;
      border-bottom: 1px solid $background-color-dark;
      margin-bottom: 15px;
      &:after {
        content: " ";
        width: 0;
        height: 0;
        top: 10px;
        right: 0;
        position: absolute;
        border-bottom: 20px solid $background-color-dark;
        border-right: 10px solid transparent;
        border-left: 10px solid transparent;
      }
      &:hover, &--selected {
        color: $color-text-primary;
        border-bottom: 1px solid $color-nuxt-green;
        &:after {
          border-bottom: 20px solid $color-nuxt-green;
        }
      }
      &:first-child:hover, &--selected-first {
        color: $color-text-primary;
        border-bottom: 1px solid $color-vue-green;
        &:after {
          border-bottom: 20px solid $color-vue-green;
        }
      }
      &:last-child:hover, &--selected-last {
        color: $color-text-primary;
        border-bottom: 1px solid $color-vue-grey;
        &:after {
          border-bottom: 20px solid $color-vue-grey;
        }
      }
    }
  }
  &_Content {
    width: 100%;
    @media (min-width: $--md) {
      width: 60%;
    }
    &_Title {
      line-height: 32px;
    }
    &_Description {
      text-align: justify;
      font-size: 16px;
    }
  }
}
</style>
