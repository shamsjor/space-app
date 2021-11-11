<template lang="pug">
.destination
  Nav
  .main
    p <span>01</span> PICK YOUR DESTINSTION
    img(:src="require(`../assets/destination/image-${name}.png`)", alt="alt")
  .tabs
    .names
      for el,index in [`Moon`, `Mars`, `Europa`, `Titan`]
        span(class={active: index===0}, @click="destination")= el
    .moon
      h1 MOON
      p.description See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.
      .info
        .distance
          p AVg. distance <span>384,400 km</span>
        .time
          p est. travel time <span>3 days</span>
    .mars
      h1 MARS
      p.description Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!
      .info
        .distance
          p AVg. distance <span>225 mil. km</span>
        .time
          p est. travel time <span>9 months</span>
    .europa
      h1 EUROPA
      p.description The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.
      .info
        .distance
          p AVg. distance <span>628 mil. km</span>
        .time
          p est. travel time <span>3 years</span>
    .titan
      h1 TITAN
      p.description The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.
      .info
        .distance
          p AVg. distance <span>1.6 bil. km</span>
        .time
          p est. travel time <span>7 years</span>
</template>

<script>
import Nav from "../components/navbar.vue";

export default {
  name: "Destination",
  components: {
    Nav,
  },
  data() {
    return {
      name: `moon`,
    };
  },
  methods: {
    destination(event) {
      let destinations = document.querySelectorAll(`.tabs .names span`),
        moon = document.querySelector(`.moon`),
        mars = document.querySelector(`.mars`),
        titan = document.querySelector(`.titan`),
        europa = document.querySelector(`.europa`);
      let divs = [moon, mars, europa, titan];
      destinations.forEach((element) => {
        element.classList.remove(`active`);
      });
      event.target.classList.add(`active`);
      divs.forEach((element) => {
        element.style.display = `none`;
        if (event.target.innerText === element.classList[0].toUpperCase()) {
          element.style.display = `block`;
          this.name = element.classList[0].toLowerCase();
        }
      });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";
.destination {
  background-image: url("../assets/destination/background-destination-desktop.jpg");
  height: 100%;
  // position: fixed;
  width: 100%;
  // margin: -9px;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  overflow-x: hidden;
}
.main {
  // position: absolute;
  margin-top: 190px;
  margin-left: 50px;
  display: inline-block;
  p {
    font-size: 28px;
    color: white;
    letter-spacing: 4.7px;
    span {
      opacity: 0.25;
      font-weight: bold;
    }
  }
  img {
    width: 400px;
    margin-top: 15px;
    margin-left: 40px;
  }
}
.tabs {
  // position: absolute;
  display: inline-block;
  margin-left: 180px;
  width: 445px;
  height: 472px;
  .names {
    width: 285.5px;
    height: 34px;
    font-size: 16px;
    color: $secondry-color;
    display: flex;
    justify-content: space-between;
    cursor: pointer;
    text-transform: uppercase;
    letter-spacing: 2.7px;
  }
  h1 {
    font-size: 100px;
    color: white;
    margin-bottom: 14px;
    margin-top: 20px;
  }
  p.description {
    color: $secondry-color !important;
    width: 444px;
    font-size: 18px;
    border-bottom: 1px solid rgba($color: #ffff, $alpha: 0.25);
    padding-bottom: 35px;
    line-height: 32px;
  }
  .info {
    display: flex;
    justify-content: space-around;
    margin-top: 20px;
    color: $secondry-color;
    p {
      font-size: 14px;
      text-transform: uppercase;
      span {
        font-size: 28px;
        display: block;
        margin-top: 5px;
      }
    }
  }
  .mars,
  .titan,
  .europa {
    display: none;
  }
}
@media (max-width: 991px) {
  .destination {
    background-image: url("../assets/destination/background-destination-tablet.jpg");
  }
  .main {
    display: block;
    margin-top: 40px;
    img {
      margin-top: 60px;
      margin-left: 160px;
    }
  }
  .tabs {
    display: block;
    text-align: center;
    margin-top: 40px;
    .names {
      width: 100%;
    }
  }
}
@media (max-width: 767px) {
  .destination {
    background-image: url("../assets/destination/background-destination-mobile.jpg");
  }
  .main {
    p {
      font-size: 15px;
    }
    img {
      width: 60%;
      margin-left: 20%;
    }
  }
  .tabs {
    margin-left: 3%;
    .names {
      width: 75%;
    }
    h1 {
      margin-left: -77px !important;
    }
    .description {
      width: 80% !important;
      // font-size: 14px;
    }
    .info {
      display: block;
      text-align: center;
      margin-left: -65px;
      .distance {
        margin-bottom: 20px;
      }
    }
  }
}
</style>
