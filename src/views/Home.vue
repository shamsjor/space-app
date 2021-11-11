<template lang="pug">
.home
  Nav
  .text
    p So, you want to travel to
    span Space
    p Let’s face it; if you want to go to space, you might as well genuinely go to outer space and not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly out of this world experience!
  .explore
    router-link(to="/Destination") Explore
</template>

<script>
import Nav from "../components/navbar.vue";
export default {
  name: "Home",
  components: {
    Nav,
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";
.home {
  background-image: url("../assets/home/background-home-desktop.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  overflow-x: hidden;
  @media (max-width: 991px) {
    .text {
      text-align: center;
      margin-top: 60px !important;
      margin-left: 245px !important;
      p:first-child {
        margin-bottom: 0px !important;
      }
      p:last-child {
        margin-top: 0px !important;
      }
    }
    .explore {
      top: -11px !important;
      left: 310px !important;
    }
  }
  @media (max-width: 767px) {
    .text {
      margin-left: 3% !important;
      p:first-child {
        font-size: 18px !important;
        margin-left: -10px;
      }
      span {
        font-size: 100px !important;
        margin-left: -70px !important;
      }
      p:last-child {
        font-size: 14px -70px !important;
        width: 80% !important;
      }
    }
    .explore {
      left: 14% !important;
    }
  }
  .text {
    width: 450px;
    height: 382px;
    margin-top: 197px;
    margin-left: 165px;
    span {
      font-size: 150px;
      color: white;
      text-transform: uppercase;
    }
  }
  .text p:first-child {
    width: 400px;
    height: 34px;
    font-size: 28px;
    letter-spacing: 4.72px;
    color: $secondry-color;
    margin-bottom: 14px;
  }
  .text p:last-child {
    height: 128px;
    font-size: 18px;
    line-height: 32px;
    color: $secondry-color;
    margin-top: 30px;
  }
  .explore:hover {
    box-shadow: rgba(#ffff, 0.1) 0px 0px 0px 50px;
  }
  .explore {
    position: relative;
    bottom: 241px;
    left: 70%;
    width: 274px;
    height: 274px;
    border-radius: 50%;
    background-color: white;
    a {
      position: absolute;
      top: 47%;
      color: $primary-color;
      left: 107px;
      font-size: 18px;
    }
  }
}
@media (max-width: 991px) {
  .home {
    background-image: url("../assets/home/background-home-tablet.jpg");
    background-repeat: no-repeat;
    background-size: cover;
  }
}
@media (max-width: 767px) {
  .home {
    background-image: url("../assets/home/background-home-mobile.jpg");
    background-repeat: no-repeat;
    background-size: cover;
  }
}
</style>
