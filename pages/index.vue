<template>
  <div>
    <section id="home" class="w3l-banner py-5">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-6 col-sm-12 mt-lg-0 mt-4 mt-sm-5">
            <span class="title-small">{{ hello }}</span>
            <h1 class="mb-2 title">
              <span>{{ me }}</span> {{ data.main.name }}
            </h1>
            <p>{{ data.main.occupation }}</p>
            <div class="mt-sm-5 mt-4">
              <nuxt-link
                :to="localePath('/contact')"
                class="btn btn-primary btn-style mr-2"
              >
                {{ $t('hireMe') }}
              </nuxt-link>
              <nuxt-link
                :to="localePath('/projects')"
                class="btn btn-outline-primary btn-style mr-2"
              >
                {{ $t('projects') }}
              </nuxt-link>
            </div>
          </div>
          <div class="col-lg-6 col-md-8 col-sm-10 mt-lg-0 mt-4">
            <div class="img-effect text-lg-center">
              <img :src="data.main.image" alt="myphoto" class="img-fluid" />
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="w3l-index3" id="about">
      <div class="midd-w3 py-5">
        <div class="container py-lg-5 py-md-3">
          <div class="row">
            <div class="col-lg-4">
              <div class="position-relative">
                <img
                  :src="data.main.fullimage"
                  alt=""
                  class="radius-image img-fluid"
                />
              </div>
            </div>
            <div class="col-lg-8 mt-lg-0 mt-5">
              <h5 class="title-small mb-2">{{ whoAmI }}</h5>
              <h3 class="title-big">
                {{ me }} <b>{{ data.main.name }}</b
                >, a {{ data.main.occupation }}
              </h3>
              <p class="mt-4">{{ data.main.bio }}</p>
              <a
                :href="data.main.resumedownload"
                target="_blank"
                class="btn btn-style btn-primary mt-lg-5 mt-4"
                >{{ $t('downloadResume') }}</a
              >
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="py-5 w3l-resume">
      <div class="container py-lg-5 py-3">
        <h5 class="title-small mb-2">{{ data.main.quotes1.sectiontitle }}</h5>
        <h3 class="title-big mb-4">{{ data.main.quotes1.title }}</h3>
        <p>
          {{ data.main.quotes1.description }}
        </p>
        <div class="mt-5">
          <a
            :href="data.main.resumedownload"
            target="_blank"
            class="btn btn-style btn-primary"
            >{{ $t('downloadResume') }}</a
          >
        </div>
      </div>
    </div>

    <section class="w3l-services">
      <div class="blog py-1" id="services">
        <div class="container py-lg-5">
          <h5 class="title-small text-center">{{ services }}</h5>
          <h3 class="title-big text-center mb-sm-5 mb-4">{{ whatIDo }}</h3>
          <div class="row">
            <div
              class="col-md-4 col-sm-12 col-xs-12"
              v-for="service in data.services.services"
              v-bind:key="service.no"
            >
              <div class="item">
                <div class="card">
                  <div class="box-wrap">
                    <div class="icon">
                      <span class="fa fa-pencil-square-o"></span>
                    </div>
                    <h4 class="number">{{ service.no }}</h4>
                    <h4>
                      <a>{{ service.title }}</a>
                    </h4>
                    <p>{{ service.description }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="mt-5 text-more">
            <p class="mt-4 pt-3 sample text-center"></p>
          </div>
        </div>
      </div>
    </section>
    <section class="w3l-index5" id="about">
      <div class="new-block py-1">
        <div class="container py-lg-5">
          <div class="middle-section text-center">
            <h5 class="title-small mb-2">
              {{ data.main.quotes2.sectiontitle }}
            </h5>
            <div class="section-width">
              <h3 class="title-big">
                {{ data.main.quotes2.title }}
              </h3>
              <p class="mt-3">
                {{ data.main.quotes2.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="w3l-grid-quote text-center py-5">
      <div class="container py-3">
        <h6 class="title-small">{{ getInTouch }}</h6>
        <h3 class="title-big mb-md-5 mb-4">{{ letsStart }}</h3>
        <router-link
          :to="localePath('/myself')"
          class="btn btn-style btn-primary mr-2"
          >{{ $t('moreAboutMe') }}
        </router-link>
        <router-link
          :to="localePath('/contact')"
          class="btn btn-style btn-outline-primary"
          >{{ $t('getInTouch') }}</router-link
        >
      </div>
    </section>
  </div>
</template>

<script>
import data from '~/static/api/data.json';
export default {
  name: 'index',
  data() {
    return {
      data: data[this.$i18n.localeProperties.code]
    };
  },
  head() {
    return {
      title: 'Home : ' + this.data.main.name,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'My custom description'
        }
      ]
    };
  }
};
</script>
