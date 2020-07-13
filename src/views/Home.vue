<template>
  <div v-if="loading">
    <Preloading />
  </div>
  <div v-else>
    <div class="home animated fadeIn">
      <div class="title">
        <h1>WHEATER</h1>
        <h2>Select a city</h2>
      </div>
      <img alt="Vue logo" src="../assets/images/logo.png" class="logo">
      <div class="menu">
        <div class="container">
          <!-- <router-link to="/">Home</router-link> -->
          <router-link to="/dallol">Dallol</router-link>
          <router-link to="/fairbanks">Fairbanks</router-link>
          <router-link to="/londres">Londres</router-link>
          <router-link to="/recife">Recife</router-link>
          <router-link to="/vancouver">Vancouver</router-link>
          <router-link to="/yakutsk">Yakutsk</router-link>
        </div>
      </div>
      <router-view/>
    </div>
  </div>
</template>

<script>
import Preloading from '../components/Preloading.vue'

export default {
  name: 'Home',
  components: {
    Preloading
  },
  data () {
    return {
      loading: true
    }
  },
  methods: {
    endLoadAnimation () {
      setTimeout(() => {
        this.loading = false
      }, 1500)
    }
  },
  mounted () {
    this.endLoadAnimation()
  }
}

</script>
