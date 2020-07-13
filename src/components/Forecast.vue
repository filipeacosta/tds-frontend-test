<template>
  <div class="page internal animated fadeIn"
    v-if="currentWeather && currentWeather.cod == 200"
    :class="currentWeather.weather[0].main.toLowerCase()"
  >
    <div class="menu">
        <router-link to="/"><i class="fas fa-arrow-left"></i></router-link>
    </div>
    <router-view/>

    <div class="container">
      <section>
        <div class="title-city">
          <h1>{{ currentWeather.name }}</h1>
          <h2>{{ currentWeather.weather[0].main.toLowerCase() }}</h2>
        </div>
        <div class="temperature">
          <h3>{{ currentWeather.main.temp.toFixed(0) }}</h3>
          <span class="celcius">°C</span>
          <div class="oscillation">
            <span><i class="fas fa-arrow-up"></i> {{ currentWeather.main.temp_max.toFixed(0) }}°</span>
            <span><i class="fas fa-arrow-down"></i> {{ currentWeather.main.temp_min.toFixed(0) }}°</span>
          </div>
        </div>
        <div class="icon-temperature">
          <i class="owi" :class="currentWeather.weather[0].main.toLowerCase()"></i>
        </div>
      </section>
      <section>
        <div class="schedules">
          <div class="schedule dawn">
            <p>dawn</p>
            <i class="fas fa-cloud"></i>
            <span>13° C</span>
          </div>
          <div class="schedule morning">
            <p>morning</p>
            <i class="fas fa-cloud"></i>
            <span>13° C</span>
          </div>
          <div class="schedule afternoon">
            <p>afternoon</p>
            <i class="fas fa-cloud"></i>
            <span>13° C</span>
          </div>
          <div class="schedule night">
            <p>night</p>
            <i class="fas fa-cloud"></i>
            <span>13° C</span>
          </div>
        </div>
        <div class="informations">
          <div class="information">
            <p>wind speed</p>
            <strong>{{ currentWeather.wind.speed }}m/s</strong>
          </div>

          <div class="information">
            <p>sunrise</p>
            <strong>{{ timestampToDate(currentWeather.sys.sunrise ) | moment("h:mm A") }}</strong>
          </div>

          <div class="information">
            <p>sunset</p>
            <strong>{{ timestampToDate(currentWeather.sys.sunset ) | moment("HH:mm A") }}</strong>
          </div>

          <div class="information">
            <p>humidity</p>
            <strong>{{ currentWeather.main.humidity }}%</strong>
          </div>
        </div>
      </section>
    </div>
  </div>
  <div v-else><Preloading /></div>
</template>

<script>

import Constants from '../constants'
import axios from 'axios'
import VueMoment from 'vue-moment'
import Preloading from './Preloading'
import '@fortawesome/fontawesome-free/css/all.css'

export default {
  components: {
    Preloading
  },
  directives: {
    moment: VueMoment
  },
  props: {
    currentCity: String
  },
  data () {
    return {
      currentWeather: null,
      currentCountry: 'world',
      unit: 'metric',
      currentIcon: null,
      loading: true
    }
  },
  methods: {
    getWeather () {
      axios
        .get(
          Constants.URL_API +
          'q=' + this.currentCity + ',' + this.currentCountry +
          '&units=' + this.unit
        )
        .then(response => {
          this.currentWeather = response.data
        })
        .catch(function (error) {
          console.log(error)
        })
    },
    timestampToDate: function (timestamp) {
      var date = new Date(timestamp * 1000)
      return date.toString()
    },
    endLoadAnimation () {
      setTimeout(() => {
        this.loading = false
      }, 1500)
    }
  },
  mounted () {
    this.getWeather()
    this.endLoadAnimation()
  }
}
</script>
