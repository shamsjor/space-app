<template lang="pug">
mixin tech(name, description)
  div(class=name)
    h1=name
    p(class="description")=description
.technology
  Nav
  .tech <span>03</span> space launch 101
  .tabs
    for el,index in [1, 2, 3]
      span(class={active: index===0},@click="tec")= el
  .text
    p.term the terminology ...
    .terms
      +tech("Launch vehicle","A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a payload from Earth's surface to space, usually to Earth orbit or beyond. Our WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall, it's quite an awe-inspiring sight on the launch pad!")
      +tech("Spaceport", "A spaceport or cosmodrome is a site for launching (or receiving) spacecraft, by analogy to the seaport for ships or airport for aircraft. Based in the famous Cape Canaveral, our spaceport is ideally situated to take advantage of the Earth’s rotation for launch.")
      +tech("Space capsule", "A space capsule is an often-crewed spacecraft that uses a blunt-body reentry capsule to reenter the Earth's atmosphere without wings. Our capsule is where you'll spend your time during the flight. It includes a space gym, cinema, and plenty of other activities to keep you entertained.")
  img(:src="require(`../assets/technology/image-${name}-portrait.jpg`)", alt="alt",class="portrait")
  img(:src="require(`../assets/technology/image-${name}-landscape.jpg`)", alt="alt",class="landscape")



</template>
<script>
import Nav from "../components/navbar.vue";
export default {
  name: "Technology",
  components: {
    Nav,
  },
  data() {
    return {
      name: `launch-vehicle`,
    };
  },
  methods: {
    tec(e) {
      let tabs = document.querySelectorAll(`.tabs span`),
        techs = document.querySelectorAll(`.text .terms div`);
      tabs.forEach((element) => {
        element.classList.remove(`active`);
      });
      e.target.classList.add(`active`);
      techs.forEach((element, index) => {
        element.style.display = `none`;
        if (index + 1 == e.target.innerText) {
          element.style.display = `block`;

          this.name = `${element.classList[`value`]
            .toLowerCase()
            .split(` `)
            .join(`-`)}`;
          console.log(element.classList);
        }
      });
    },
  },
};
</script>
<style lang="scss" scoped>
.technology {
  background-image: url("../assets/technology/background-technology-desktop.jpg");
  background-position: center;
  background-size: cover;
  overflow-x: hidden;
  background-repeat: no-repeat;
  .tech {
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
  .text {
    width: 470px;
    display: inline-block;
    margin-left: 70px;
    p.term {
      font-size: 16px;
      letter-spacing: 2.7;
      color: #d0d6f9;
      text-transform: uppercase;
    }
    .terms {
      h1 {
        font-size: 52px;
        color: white;
        text-transform: uppercase;
        font-weight: normal;
      }
      p.description {
        font-size: 18px;
        line-height: 32px;
        color: #d0d6f9;
      }
      .Space,
      .Spaceport {
        display: none;
      }
    }
  }
  .tabs {
    margin-left: 165px;
    display: inline-block;
    margin-top: 100px;
    span {
      width: 80px;
      height: 80px;
      background-color: transparent;
      color: white;
      // display: block;
      border-radius: 50%;
      border: 1px solid white;
      font-size: 32px;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
    }
    span:nth-child(2) {
      margin-top: 12px;
      margin-bottom: 12px;
    }
  }
  img.portrait {
    margin-left: 3.6%;
  }
  img.landscape {
    display: none;
  }
  span.active {
    background-color: white;
    color: #0b0d17;
  }
}
@media (max-width: 991px) {
  .technology {
    background-image: url("../assets/technology/background-technology-tablet.jpg");
    display: flex;
    flex-direction: column;
    .tech {
      margin-bottom: 30px;
      margin-left: 60px;
    }
    img.portrait {
      display: none;
    }
    img.landscape {
      display: block;
      order: 2;
    }
    .tabs {
      order: 3;
      display: flex;
      span:nth-child(2) {
        margin-left: 20px;
        margin-right: 20px;
        margin-top: 0px;
        margin-bottom: 0px;
      }
    }
    .text {
      order: 5;
      text-align: center;
      margin-top: 30px;
    }
  }
}
@media (max-width: 767px) {
  .technology {
    background-image: url("../assets/technology/background-technology-mobile.jpg");
    .tech {
      width: 100%;
      font-size: 18px;
    }
    .tabs {
      margin-left: 45px;
    }
    .text {
      margin-left: 2px;
      width: 100%;
      .terms {
        h1 {
          font-size: 40px;
        }
      }
    }
  }
}
</style>
