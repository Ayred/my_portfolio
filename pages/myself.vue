<template>
  <div>
    <section class="w3l-about-breadcrumb text-center">
      <div class="breadcrumb-bg breadcrumb-bg-about py-sm-5 py-4">
        <div class="container py-2">
          <h2 class="title">{{ $t('aboutMe') }}</h2>
          <ul class="breadcrumbs-custom-path mt-2">
            <li>
              <router-link to="/">{{ $t('home') }}</router-link>
            </li>
            <li class="active">
              <span class="fa fa-arrow-right mx-2" aria-hidden="true"></span>
              {{ $t('aboutMe') }}
            </li>
          </ul>
        </div>
      </div>
    </section>

    <section class="w3l-aboutblock1" id="about">
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
              <h5 class="title-small mb-2">
                {{ $t('helloIam') }} {{ data.main.designation }}
              </h5>
              <h3 class="title-big">
                {{ $t('having') }} {{ data.main.yearofexperience }}
                {{ $t('yearsOfExperience') }}
              </h3>
              <p class="mt-4">{{ data.main.bio }}</p>
              <div class="my-info mt-4">
                <div class="single-info">
                  <span>{{ $t('name') }}:</span>
                  <p>{{ data.main.name }}</p>
                </div>

                <div class="single-info">
                  <span>{{ $t('located') }}</span>
                  <p>
                    {{ data.main.address.city }}, {{ data.main.address.state }}
                  </p>
                </div>
                <div class="single-info">
                  <span>{{ $t('email') }}:</span>
                  <p>
                    <a
                      target="_blank"
                      :href="'mailto:' + data.main.email"
                      class="mail"
                      >{{ data.main.email }}</a
                    >
                  </p>
                </div>
              </div>
              <div class="my-social mt-lg-5 mt-4">
                <a
                  :href="data.main.resumedownload"
                  target="_blank"
                  class="btn btn-style btn-primary"
                  >{{ $t('downloadCV') }}</a
                >
                <ul class="social m-0 p-0">
                  <li
                    v-for="social in data.main.social"
                    v-bind:key="social.name"
                  >
                    <a target="_blank" :href="social.url"
                      ><span :class="social.className"></span
                    ></a>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="w3l-content-6 py-5">
      <h5 class="title-small text-center">{{ $t('technologies') }}</h5>
      <div class="content-6-mian py-lg-5 py-md-4">
        <div class="container">
          <div class="content-info-in row">
            <div class="content-gd col-lg-5">
              <h3 class="title-big mb-4">
                {{ data.resume.skillssectiontitle }}
              </h3>
              <p>
                {{ data.resume.skillssectiondescription }}
              </p>
            </div>
            <div class="content-gd col-lg-6 offset-lg-1">
              <div
                class="progress-info"
                v-for="skill in data.resume.skills"
                v-bind:key="skill.name"
              >
                <h6 class="progress-tittle">
                  <b>{{ skill.name }} :</b>
                  <font style="float: right">{{ skill.level }}</font>
                </h6>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="abouthy-img-grids">
      <div class="img-one">
        <img src="/resources/assets/images/g5.jpg" alt=" " class="img-fluid" />
      </div>
      <div class="img-one content-mid">
        <center>
          <h3 class="title-big">{{ $t('emailMeRightNow') }}</h3>
          <br />
          <a
            target="_blank"
            :href="'mailto:' + data.main.email"
            class="mail btn btn-primary"
            >{{ data.main.email }}</a
          >
        </center>
      </div>
      <div class="img-one">
        <img src="/resources/assets/images/g3.jpg" alt=" " class="img-fluid" />
      </div>
    </div>

    <section class="w3l-services">
      <div class="w3l-achievements py-5" id="services">
        <div class="container py-lg-5">
          <h5 class="title-small text-center mb-2">Education</h5>

          <div class="row">
            <div
              class="col-lg-4 item align-center m-auto"
              v-for="education in data.resume.education"
              v-bind:key="education.description"
            >
              <h3 class="title-big text-center mb-sm-5 mb-4">
                {{ $t('myEducation') }}
              </h3>
              <div class="card">
                <div class="box-wrap">
                  <div class="icon">
                    <span class="fa fa-graduation-cap"></span>
                  </div>
                  <h4>
                    <a href="">{{ education.degree }}</a>
                  </h4>
                  <p>
                    {{ $t('school') }} : {{ education.school }}<br />
                    {{ $t('graduated') }} : {{ education.graduated }}<br />
                    {{ $t('description') }} : {{ education.description }}<br />
                  </p>
                </div>
              </div>
            </div>
            <div class="col-lg-4 m-auto align-center">
              <div class="position-relative">
                <img
                  :src="data.main.graduationImage"
                  alt=""
                  class="radius-image img-fluid"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="w3l-services">
      <div class="w3l-achievements py-5" id="services">
        <div class="container py-lg-5">
          <h5 class="title-small text-center">{{ $t('specialization') }}</h5>
          <h3 class="title-big text-center mb-sm-5 mb-4">
            {{ $t('cousesAndCertifications') }}
          </h3>
          <div class="row">
            <div
              class="col-lg-3 item"
              v-for="certificate in data.resume.certifications"
              v-bind:key="certificate.name"
            >
              <div class="card">
                <a :href="certificate.url" target="_blank">
                  <div class="box-wrap">
                    <div class="icon">
                      <span class="fa fa-certificate"></span>
                    </div>
                    <h4 class="cardHeight">
                      <a>{{ certificate.certificatename }}</a>
                    </h4>
                    <p class="cardHeightD">
                      {{ $t('cousesAndCertifications') }}:
                      {{ certificate.organization }}<br />
                    </p>
                  </div>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="w3l-services">
      <div class="w3l-achievements py-5" id="services">
        <div class="container py-lg-5">
          <h5 class="title-small text-center">{{ $t('work') }}</h5>
          <h3 class="title-big text-center mb-sm-5 mb-4">
            {{ $t('myCurrentWorkExperience') }}
          </h3>
          <div class="row">
            <div
              class="col-lg-6 item"
              v-for="work in data.resume.work"
              v-bind:key="work.company"
            >
              <div class="card">
                <div class="box-wrap">
                  <div class="icon">
                    <span class="fa fa-briefcase"></span>
                  </div>
                  <h4>
                    <a href="">{{ work.title }}</a>
                  </h4>
                  <p>
                    {{ $t('company') }} : {{ work.company }}<br />
                    {{ $t('year') }} : {{ work.years }}<br />
                    {{ $t('description') }}: {{ work.description }}<br />
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
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
      title: 'About : ' + this.data.main.name,
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

<style scoped>
.cardHeight {
  height: 9.5rem;
}
.cardHeightD {
  height: 2rem;
}
</style>
