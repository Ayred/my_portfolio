<template>
  <div>
    <section class="w3l-about-breadcrumb text-center">
      <div class="breadcrumb-bg breadcrumb-bg-about py-sm-5 py-4">
        <div class="container py-2">
          <h2 class="title">Contact Me</h2>
          <ul class="breadcrumbs-custom-path mt-2">
            <li><a href="/">Home</a></li>
            <li class="active">
              <span class="fa fa-arrow-right mx-2" aria-hidden="true"></span>
              Contact
            </li>
          </ul>
        </div>
      </div>
    </section>

    <section class="w3l-contact-1 py-5">
      <div class="contacts-9 py-lg-5 py-md-4">
        <div class="container">
          <div class="d-grid contact-view">
            <div class="cont-details">
              <div class="cont-top margin-up">
                <div class="cont-left text-center">
                  <span class="fa fa-envelope-o text-primary"></span>
                </div>
                <div class="cont-right">
                  <h6>Email Me</h6>
                  <p>
                    <a :href="'mailto:' + data.main.email" class="mail">{{
                      data.main.email
                    }}</a>
                  </p>
                </div>
              </div>
              <div class="cont-top margin-up">
                <div class="cont-left text-center">
                  <span class="fa fa-map-marker text-primary"></span>
                </div>
                <div class="cont-right">
                  <h6>Location</h6>
                  <p>
                    {{ data.main.address.city }}, {{ data.main.address.state }}.
                  </p>
                </div>
              </div>
            </div>
            <div class="map-content-9">
              <div
                class="cont-top m-5"
                v-for="social in data.main.social"
                v-bind:key="social.name"
              >
                <div class="cont-left text-center">
                  <span :class="social.className"></span>
                </div>
                <div class="cont-right">
                  <h6>{{ social.name }}</h6>
                  <p>
                    <a target="_blank" :href="social.url"
                      ><font size="4px">{{ social.url }}</font></a
                    >
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="map-iframe">
      <iframe
        :src="data.main.mapaddress"
        width="100%"
        height="400"
        frameborder="0"
        style="border: 0px"
        allowfullscreen=""
      ></iframe>
    </div>
  </div>
</template>

<script>
import data from '~/static/api/data.json';
export default {
  name: 'index',
  data() {
    return {
      data: data
    };
  },
  head() {
    return {
      title: 'Contact : ' + this.data.main.name,
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
