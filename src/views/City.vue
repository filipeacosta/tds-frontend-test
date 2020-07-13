<template>
    <Forecast v-if="currentCity" :currentCity="currentCity" />
</template>

<script>

import Forecast from '../components/Forecast'

export default {
  components: {
    Forecast
  },
  data () {
    return {
      currentCity: ''
    }
  },
  mounted () {
    this.currentCity = this.$route.params.city
  },
  watch: {
    $route (to, from) {
      this.currentCity = to.params.city
    }
  }
}
</script>
