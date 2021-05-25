<template>
  <div class="page">
    <div class="page-container">
      <div class="navbar">
        <ul>
          <li class="item-active"><a href="#">HOME</a></li>
          <li class="item-inactive"><a href="#">WORK</a></li>
          <li class="item-inactive"><a href="#">ARTICLES</a></li>
          <li class="item-inactive"><a href="#">CONTACT</a></li>
        </ul>
        <div class="horizontal-divider"></div>
      </div>
      <div class="home-card">
        <div class="face">
          <img src="svg/face.svg" alt="SVG of my face">
        </div>
        <!-- <div class="vertical-divider"></div> -->
        <div class="greeting">
          <h1>Hello,</h1>
          <h2>I'm Paul</h2>
          <h3>web designer & student</h3>
        </div>
      </div>
      <div class="arrow-down">
        <font-awesome-layers class="fa-6x" style="cursor: pointer">
          <a href="#">
            <font-awesome-icon icon="arrow-alt-circle-down"/>
          </a>
        </font-awesome-layers>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style lang="scss" scoped>
.navbar {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 1rem;

  .horizontal-divider {
    width: 90%;
    padding-top: 2em;
    border-bottom: 4px solid $color_primary_darker;
  }

  ul {
    display: flex;
    width: 100%;
    justify-content: space-between;
    padding: 0;

    li {
      list-style-type: none;
      border-radius: 4px;

      &:hover {
        cursor: pointer;
      }

      a {
        display: flex;
        justify-content: center;

        font-family: Overpass;
        font-size: 3vw;
        font-weight: 800;

        padding-top: 1vh;
        padding-left: 3vw;
        padding-right: 3vw;

        box-shadow: 6px 6px 4px rgba($color: $color_black, $alpha: 0.25);

        text-decoration: none;
      }
    }

    .item-active {
      a { color: $color_white; }
      background-color: $color_signal;
    }

    .item-inactive {
      a { color: $color_primary_darker; }
      background-color: $color_primary_lighter;
    }
  }
}

.home-card {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1;

  .face {
    padding-right: 3rem;

    img {
      height: 30rem;
    }
  }

  .vertical-divider {
    height: 12rem;
    border-left: 3px solid $color_primary_lighter;
  }

  .greeting {
    padding-left: 3rem;

    h3 {
      padding: 0.125em 0.25em 0.125em 0.25em;
      font-family: Chivo;
      font-weight: 400;
      font-size: 2.75em;
      letter-spacing: 0.125em;
      background-color: $color_signal_alt;
    }

    h1, h2 {
      font-size: 8em;
      font-family: 
      Overpass,
      -apple-system,
      BlinkMacSystemFont,
      'Segoe UI',
      Roboto,
      'Helvetica Neue',
      Arial,
      sans-serif;
      font-weight: 700;
      letter-spacing: -0.08em;
    }
  }
}

.arrow-down {
  display: flex;
  justify-content: center;

  a {
    display: inline-block;
    height: 100%;
    width: 100%;

    background-color: $color_white;
    border-radius: 50%;

    color: $color_signal;

    &:hover {
      background-color: transparent;
    }

    svg {
      box-sizing: border-box;

      &:hover {
        animation: arrowBounce 1.25s infinite;
      }
    }
  }
}

@keyframes arrowBounce {
  0% {
    transform: translate(0, 0);
  }
  20% {
    transform: translateY(10px);
  }
  40% {
    transform: translate(0, 0);
  }
}

.page {
  height: 100vh;
  width: 100vw;
  
  background-color: $color_primary;
  border: 4rem solid $color_primary;
}

.page-container {
  display: flex;
  flex-direction: column;  

  height: 100%;
  padding: 1.75rem 2rem;

  color: $color_white;
  // border: 4px solid $color_white;
}

</style>
