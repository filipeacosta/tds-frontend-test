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

<style lang="scss">
  .home {
    width: 100%;
    height: 100%;
    background: #0f0f0f;
    position: absolute;
    top: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    align-content: center;
    flex-wrap: wrap;

    .title {
        width: 100%;
        text-align: center;
        margin-bottom: 2rem;

        h1 {
            color: #fff;
            margin-bottom: 1rem;
        }

        h2 {
            color: #ddd;
            font-weight: 400;
            margin: 0;
        }
    }

    .logo {
        width: 15rem;
        margin: 2rem 0 3rem;
        -webkit-animation: rotation 30s infinite linear;
    }

    .menu {
        width: 100%;

        .container {
            padding: 0 2rem;
            max-width: 40rem;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;

            a {
                display: block;
                width: 33.333%;
                color: #fff;
                text-decoration: none;
                font-size: 2rem;
                margin-bottom: 2rem;
                transition: .3s;
                position: relative;
                &:before{
                    transition: .3s;
                    content:'';
                    display: block;
                    width: 0;
                    height: .1rem;
                    position: absolute;
                    top:50%;
                    left: 50%;
                    transform:translate(-50%, -50%);
                    background: #fff;
                    zoom: .6;
                }
                &:hover {
                    &:before{
                        width: 80%;
                    }
                }
            }
        }
    }

    @-webkit-keyframes rotation {
        from {
            -webkit-transform: rotate(0deg);
        }

        to {
            -webkit-transform: rotate(359deg);
        }
    }
}
</style>
