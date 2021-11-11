<template lang="pug">
mixin member(name, role, bio)
  div(class=`${name}`)
    h1= role
    .name= name
    p.bio= bio

.crew 
  Nav
  .team <span>02</span> meet your crew
  .main
    .content
      +member("Douglas Hurley", "Commander", "Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.")
      +member("Mark Shuttleworth", "Mission Specialist","Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.")
      +member("Victor Glover", "Pilot","Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.")
      +member("Anousheh Ansari", "Flight Engineer","Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.")
      .dots
        for el,index in ["Douglas Hurley","Mark Shuttleworth","Victor Glover","Anousheh Ansari"]
          span(class={active: index===0}, @click="slider")=el
    .member-im
      img(:src="require(`../assets/crew/image-${name}.png`)", alt="alt")
</template>

<script>
import Nav from "../components/navbar.vue";
export default {
  name: "Crew",
  components: {
    Nav,
  },
  data() {
    return {
      name: `douglas-hurley`,
    };
  },
  methods: {
    slider(e) {
      let dots = document.querySelectorAll(`.dots span`),
        Douglas = document.querySelector(`.Douglas`),
        Mark = document.querySelector(`.Mark`),
        Victor = document.querySelector(`.Victor`),
        Anousheh = document.querySelector(`.Anousheh`),
        members = [Douglas, Mark, Victor, Anousheh];
      dots.forEach((element) => {
        element.classList.remove(`active`);
      });
      e.target.classList.add(`active`);
      members.forEach((element) => {
        element.style.display = `none`;
        if (element.classList.value === e.target.innerText) {
          element.style.display = `block`;
          this.name = `${element.classList[0].toLowerCase()}-${element.classList[1].toLowerCase()}`;
        }
      });
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/scss/main.scss";
.crew {
  background-image: url("../assets/crew/background-crew-desktop.jpg");
  background-position: center;
  background-size: cover;
  overflow-x: hidden;
  background-repeat: no-repeat;
  .main {
    display: flex;
  }
  .team {
    font-size: 28px;
    letter-spacing: 4.7px;
    color: white;
    margin-left: 166.5px;
    text-transform: uppercase;
    margin-top: 30px;
    span {
      opacity: 50%;
      font-weight: bold;
    }
  }
  .content {
    margin-top: 100px;
    h1 {
      margin-left: 166.5px;
      font-size: 32px;
      color: white;
      opacity: 50%;
      text-transform: uppercase;
    }
    .name {
      font-size: 56px;
      color: white;
      margin-left: 166.5px;
      text-transform: uppercase;
      margin-bottom: 40px;
      margin-top: 20px;
    }
    p.bio {
      width: 444px;
      font-size: 18px;
      line-height: 32px;
      color: #d0d6f9;
      margin-left: 166.5px;
    }
    .Anousheh,
    .Mark,
    .Victor {
      display: none;
    }
  }
  .member-im {
    margin-left: 80px;
  }
  .dots {
    margin-left: 166px;
    height: 47px;
    display: flex;
    width: 132px;
    justify-content: space-between;
    margin-top: 30px;
    span {
      background-color: white;
      width: 15px;
      height: 15px;
      border-radius: 50%;
      display: block;
      color: transparent;
      opacity: 17%;
      cursor: pointer;
    }
  }
}
@media (max-width: 991px) {
  .crew {
    background-image: url("../assets/crew/background-crew-tablet.jpg");
    .main {
      display: block;
      .content {
        text-align: center;
        .bio {
          margin-left: 300px;
        }
        .dots {
          margin-left: 450px;
        }
      }
    }
  }
}
@media (max-width: 767px) {
  .crew {
    background-image: url("../assets/crew/background-crew-mobile.jpg");
    .team {
      margin-left: 20px;
      width: 100%;
      font-size: 20px;
    }
    .main {
      display: flex;
      flex-direction: column;
      .content {
        order: 2;
        margin-left: -200px;
        .bio {
          margin-left: 204px;
          width: 60%;
        }
        .dots {
          margin-left: 300px;
        }
      }
      .member-im {
        border-bottom: 1px solid $secondry-color;
        margin-left: 44px;
        width: 80%;
        margin-top: 30px;
        img {
          width: 80%;
          margin-left: 20px;
        }
      }
    }
  }
}
</style>
