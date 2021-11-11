<template lang="pug">
nav
  .logo
    img(src="../assets/shared/logo.svg", alt="alt")
  .menu-icon
    img(src="../assets/shared/icon-hamburger.svg", alt="alt", @click="open")
  .list
    .close
      img(src="../assets/shared/icon-close.svg", alt="alt", @click="close")
    ul
      for el,index in [`Home`,`Destination`, `Crew`, `Technology`]
        router-link(to=`/${el}`, tag="li")
          span.order= `0${index}` 
          span= `${el}` 
</template>

<script>
export default {
  name: "Nav",
  methods: {
    open() {
      let list = document.querySelector(`.list`),
        close = document.querySelector(`.close`);
      list.style.display = `block`;
      close.style.display = `flex`;
    },
    close() {
      let list = document.querySelector(`.list`);
      list.style.display = `none`;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/scss/main.scss";
nav {
  @include display();
  position: relative;
  .logo {
    margin-top: 64px;
    margin-left: 55px;
  }
  .menu-icon {
    margin-top: 64px;
    margin-right: 25px;
    display: none;
  }
  .list::before {
    content: "";
    position: absolute;
    width: 473px;
    height: 1px;
    left: 167px;
    color: white;
    opacity: 0.25;
    mix-blend-mode: normal;
  }
  @media (max-width: 991px) {
    .list {
      width: 450px !important;
    }
    ul {
      width: 356px !important;
      margin-left: 10px !important;
      a {
        font-size: 14px;
        letter-spacing: 2.3px !important;
        span:first-child {
          display: none;
        }
      }
    }
  }
  @media (max-width: 767px) {
    .list {
      display: none;
      width: 250px !important;
      position: fixed;
      right: 0;
      height: 100% !important;
      z-index: 1;
      margin-top: 0px !important;
      ul {
        flex-direction: column;
        width: 356px !important;
        margin-left: 10px !important;
        margin-top: 70px !important;
        a {
          span:first-child {
            display: inline-block;
          }
        }
        a.router-link-active span:last-child {
          border-bottom: none;
        }
      }
    }
    .menu-icon {
      display: block;
    }
  }
  .list {
    color: white;
    width: 830px;
    height: 96px;
    background-color: rgba($color: #ffff, $alpha: 0.04);
    backdrop-filter: blur(81.5485px);
    margin-top: 40px;
    border: 1px solid #979797;
    .close {
      display: none;
      justify-content: end;
      margin-top: 30px;
      margin-right: 25px;
    }
    ul {
      @include display();
      width: 542px;
      height: 19px;
      margin-bottom: 39px;
      margin-top: 22px;
      margin-left: 123px;
      margin-right: 169px;
      a {
        padding: 20px;
        letter-spacing: 2.7px;
        font-weight: 400;
        span.order {
          margin-right: 11px;
        }
      }
    }
  }
}
</style>

<style lang="scss">
a {
  span:last-child {
    padding-bottom: 34px;
  }
  span:last-child:hover {
    border-bottom: rgba(#ffff, 0.5) 3px solid;
  }
}
a.router-link-active span:last-child {
  border-bottom: 3px solid white;
}
</style>
