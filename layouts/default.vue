<template>
  <div>
    <header id="site-header" class="fixed-top">
      <div class="container">
        <nav class="navbar navbar-expand-lg stroke">
          <nuxt-link to="/" class="navbar-brand">
            <span class="fa fa-laptop"></span> {{ data.main.shortname }}
          </nuxt-link>

          <button
            ref="navbutton"
            class="navbar-toggler collapsed bg-gradient"
            type="button"
            data-toggle="collapse"
            data-target="#navbarTogglerDemo02"
            aria-controls="navbarTogglerDemo02"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon fa icon-expand fa-bars"></span>
            <span class="navbar-toggler-icon fa icon-close fa-times"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
            <ul class="navbar-nav ml-auto">
              <li
                class="nav-item"
                :class="{ active: isCurrentRoute(localePath('/')) }"
              >
                <nuxt-link :to="localePath('/')" class="nav-link"
                  >{{ $t('welcome') }}
                  <span class="sr-only">(current)</span></nuxt-link
                >
              </li>
              <li
                class="nav-item"
                :class="{ active: isCurrentRoute(localePath('/myself')) }"
              >
                <nuxt-link :to="localePath('/myself')" class="nav-link">{{
                  $t('aboutMe')
                }}</nuxt-link>
              </li>
              <li
                class="nav-item"
                :class="{ active: isCurrentRoute(localePath('/projects')) }"
              >
                <nuxt-link :to="localePath('/projects')" class="nav-link">{{
                  $t('projects')
                }}</nuxt-link>
              </li>
              <li
                class="nav-item"
                :class="{ active: isCurrentRoute(localePath('/contact')) }"
              >
                <nuxt-link :to="localePath('/contact')" class="nav-link">{{
                  $t('contact')
                }}</nuxt-link>
              </li>
            </ul>
          </div>

          <div class="col-sm-12 col-md-2 text-center">
            <nuxt-link :to="switchLocalePath('en')"
              ><country-flag country="us" />&nbsp;
            </nuxt-link>
            <nuxt-link :to="switchLocalePath('es')"
              ><country-flag country="mx" />&nbsp;
            </nuxt-link>
            <nuxt-link :to="switchLocalePath('pt')"
              ><country-flag country="br" />&nbsp;
            </nuxt-link>
          </div>

          <div class="mobile-position">
            <nav class="navigation">
              <div class="theme-switch-wrapper">
                <label class="theme-switch" for="checkbox">
                  <input type="checkbox" id="checkbox" />
                  <div class="mode-container">
                    <i class="gg-sun"></i>
                    <i class="gg-moon"></i>
                  </div>
                </label>
              </div>
            </nav>
          </div>
        </nav>
      </div>
    </header>

    <nuxt />

    <section class="w3l-footer py-sm-5 py-4">
      <div class="container">
        <div class="footer-content">
          <div class="row">
            <div class="col-lg-8 footer-left">
              <p class="m-0">
                {{ data.main.shortname }}{{ $t('copyright') }}
                <a href="http://tatatato.com/" target="_blank">TATATATO </a>
              </p>
            </div>
            <div
              class="col-lg-4 footer-right text-lg-right text-center mt-lg-0 mt-3"
            >
              <ul class="social m-0 p-0">
                <li
                  v-for="socaildata in data.main.social"
                  v-bind:key="socaildata.name"
                >
                  <a target="_blank" :href="socaildata.url"
                    ><span :class="socaildata.className"></span
                  ></a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <button onclick="topFunction()" id="movetop" title="Go to top">
        <span class="fa fa-angle-up"></span>
      </button>
    </section>
  </div>
</template>
<script>
import data from '~/static/api/data.json';
import CountryFlag from 'vue-country-flag';
export default {
  components: {
    CountryFlag
  },
  name: 'index',
  data() {
    return {
      data: data[this.$i18n.localeProperties.code]
    };
  },
  watch: {
    '$route.path'(val) {
      if (!this.$refs.navbutton.classList.contains('collapsed'))
        this.$refs.navbutton.click();
    }
  },
  methods: {
    isCurrentRoute(route) {
      return this.$route.path == route;
    }
  }
};
</script>
