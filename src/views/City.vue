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

<style lang="scss">
  .page {
    color: #fff;
    position: absolute;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    &.clear {
        background: rgb(87, 202, 219);
        background: linear-gradient(180deg, rgba(87, 202, 219, 1) 0%, rgba(59, 161, 180, 1) 70%);

        .menu {
            a {
                color: #fff;
            }
        }

        .informations {
            .information {
                &:before {
                    background: #fff !important;
                }
            }
        }
    }
    &.clouds,
    &.rain,
    &.thunderstorm {
        background: rgb(97, 105, 120);
        background: linear-gradient(180deg, rgba(97, 105, 120, 1) 0%, rgba(59, 67, 83, 1) 70%);

        .loading {
            background: rgb(97, 105, 120);
            background: linear-gradient(180deg, rgba(97, 105, 120, 1) 0%, rgba(59, 67, 83, 1) 70%);
        }

        .menu {
            a {
                color: #fff;
            }
        }
    }
    &.snow{
        background: rgb(225,224,225);
        background: linear-gradient(180deg, rgba(225,224,225,1) 0%, rgba(166,166,166,1) 70%);
        color:#000;
        .menu {
            a {
                color: #000;
            }
        }

        .informations {
            .information {
                p,
                strong{
                    color:#000!important;
                }
                &:before {
                    background: #000 !important;
                }
            }
        }
    }
    &.internal {
        .menu {
            position: absolute;
            top: 2.5rem;
            left: 4rem;

            a {
                font-size: 3rem;
            }
        }

        .title-city {
            h1 {
                text-transform: uppercase;
                font-weight: 450;
                margin-bottom: -2rem;
                letter-spacing: .2rem;
            }

            h2 {
                font-weight: 300;
            }
        }

        .temperature {
            display: flex;
            align-items: flex-end;
            margin: 3rem auto;
            position: relative;
            max-width: 16.5rem;

            .celcius {
                position: absolute;
                top: -1.3rem;
                right: 0;
                font-size: 2.8rem;
            }

            h3 {
                font-weight: 400;
                font-size: 10rem;
                line-height: 7rem;
                margin: 0;
            }

            .oscillation {
                margin-left: 1rem;

                span {
                    display: block;
                    width: 100%;
                    i{
                        opacity: .5;
                    }
                }
            }
        }

        .icon-temperature {
            margin-bottom: 4rem;
            i {
                font-size: 10rem;
            }
        }

        .schedules {
            display: flex;
            align-items: center;
            justify-content: center;

            .schedule {
                margin-right: 2rem;

                p {
                    margin: 0;
                }

                i {
                    font-size: 3.5rem;
                    margin: 1rem;
                }

                span {
                    display: block;
                    width: 100%;
                }

                &:last-child {
                    margin-right: 0;
                }
            }
        }

        .informations {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 4rem;

            .information {
                position: relative;
                padding: 0 1.5rem;

                p {
                    font-size: 1.4rem;
                    color: #ddd;
                    margin-bottom: .8rem;
                }

                strong {
                    color: #fff;
                    font-size: 1.6rem;
                    font-weight: 300;
                }

                &:before {
                    content: '';
                    display: block;
                    position: absolute;
                    width: .1rem;
                    height: 2rem;
                    background: #596270;
                    top: 50%;
                    right: 0;
                    transform: translate(0, -30%);
                }

                &:last-child {
                    &:before {
                        display: none;
                    }
                }
            }
        }
    }
}

@media (max-height:468px){
    .internal{
        .container{
            display: flex;
            align-items: center;
            section{
                transition: .3s;
                &:first-child{
                    margin-right: 3rem;
                }
            }
        }
    }
}
</style>
