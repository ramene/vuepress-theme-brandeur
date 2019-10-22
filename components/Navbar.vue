<template>
    <header class="navbar">
    <div class="flex w-full">
      <div class="flex-grow-0">
         <router-link
          :to="$localePath"
          class="home-link"
        >
          <img
            class="logo"
            v-if="$site.themeConfig.logo"
            :src="$withBase($site.themeConfig.logo)"
            :alt="$siteTitle"
          >
          <span
            ref="siteName"
            class="site-name"
            v-if="$siteTitle"
            :class="{ 'can-hide': $site.themeConfig.logo }"
          >{{ $siteTitle }}</span>
        </router-link>
      </div>
      <div class="flex-grow">
        <!-- topic placeholder -->
      </div>
      <div class="flex-grow-0">
          <div class="px-2">
            <div class="flex -mx-2">
              <div class="w-1/2">
                <!-- topic placeholder -->
              </div>
              <div class="w-1/2 pr-4">
                <div class="h-8">
                  <a href="#" class="inline-block text-sm px-4 py-2 leading-none border rounded text-brand-ice border-brand-ice hover:border-green-700 hover:text-teal-500 hover:bg-white lg:mt-0">
                    Patreon
                  </a>
                </div>
              </div>
            </div>
          </div>
            <!-- <div
            class="links"
            :style="linksWrapMaxWidth ? {
                'max-width': linksWrapMaxWidth + 'px'
            } : {}"
            >
              <div>
                <a href="#" class="inline-block text-sm px-4 py-2 leading-none border rounded text-white text-brand-ice border-brand-ice hover:border-transparent hover:text-teal-500 hover:bg-white mt-0 lg:mt-0">
                  Download
                </a>
                <a href="#" class="inline-block text-sm px-4 py-2 leading-none border rounded text-white text-brand-ice border-brand-ice hover:border-transparent hover:text-teal-500 hover:bg-white mt-0 lg:mt-0">
                  Request Demo
                </a>
              </div>
              
              <div class="fixed top-0 mt-12 text-xs font-mono text-white h-6 w-6 rounded-full flex items-center justify-center bg-gray-700 sm:bg-pink-500 md:bg-orange-500 lg:bg-green-500 xl:bg-blue-500">
                  <div class="block  sm:hidden md:hidden lg:hidden xl:hidden">al</div>
                  <div class="hidden sm:block  md:hidden lg:hidden xl:hidden">sm</div>
                  <div class="hidden sm:hidden md:block  lg:hidden xl:hidden">md</div>
                  <div class="hidden sm:hidden md:hidden lg:block  xl:hidden">lg</div>
                  <div class="hidden sm:hidden md:hidden lg:hidden xl:block">xl</div>
              </div>
            </div> -->
        </div>
      </div>
    </div>
    <div class="flex shifting">
      <div class="flex-grow-0">
        <NavLinks />
      </div>
      <div class="flex-grow">
        <!-- topic placeholder -->
      </div>
    </div>
  </header>
</template>

<script>
import AlgoliaSearchBox from '@AlgoliaSearchBox'
import SearchBox from '@SearchBox'
import SidebarButton from '@theme/components/SidebarButton.vue'
import NavLinks from '@theme/components/NavLinks.vue'

export default {
  components: { SidebarButton, NavLinks, SearchBox, AlgoliaSearchBox },

  data () {
    return {
      linksWrapMaxWidth: null
    }
  },

  mounted () {
    const MOBILE_DESKTOP_BREAKPOINT = 719 // refer to config.styl
    const NAVBAR_VERTICAL_PADDING = parseInt(css(this.$el, 'paddingLeft')) + parseInt(css(this.$el, 'paddingRight'))
    const handleLinksWrapWidth = () => {
      if (document.documentElement.clientWidth < MOBILE_DESKTOP_BREAKPOINT) {
        this.linksWrapMaxWidth = null
      } else {
        this.linksWrapMaxWidth = this.$el.offsetWidth - NAVBAR_VERTICAL_PADDING
          - (this.$refs.siteName && this.$refs.siteName.offsetWidth || 0)
      }
    }
    handleLinksWrapWidth()
    window.addEventListener('resize', handleLinksWrapWidth, false)
  },

  computed: {
    algolia () {
      return this.$themeLocaleConfig.algolia || this.$site.themeConfig.algolia || {}
    },

    isAlgoliaSearch () {
      return this.algolia && this.algolia.apiKey && this.algolia.indexName
    }
  }
}

function css (el, property) {
  // NOTE: Known bug, will return 'auto' if style value is 'auto'
  const win = el.ownerDocument.defaultView
  // null means not to return pseudo styles
  return win.getComputedStyle(el, null)[property]
}
</script>

<style lang="stylus">

$navbar-vertical-padding = 0.5rem
$navbar-horizontal-padding = 1.4rem

.navbar
  padding $navbar-vertical-padding $navbar-horizontal-padding
  line-height 1.9rem
  .logo
    height $navbarHeight - 1.4rem
    min-width $navbarHeight - 1.4rem
    margin-right 0.8rem
    vertical-align top
  .site-name
    font-size 1.3rem
    font-weight 600
    color $textColor
    position relative
  .links
    box-sizing border-box
    background-color white
    white-space nowrap
    font-size 0.7rem
    position absolute
    right $navbar-horizontal-padding
    top $navbar-vertical-padding

@media (max-width: $MQMobile)
  .navbar
    padding $navbar-vertical-padding $navbar-horizontal-padding
    line-height 1.9rem
      
    .links
      box-sizing border-box
      background-color white
      white-space nowrap
      font-size 0.7rem
      position absolute
      right $navbar-horizontal-padding
      top $navbar-vertical-padding
    .site-name
      overflow hidden
      white-space nowrap
      text-overflow ellipsis
</style>