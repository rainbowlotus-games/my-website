<template>
  <div class="page">
    <div class="page-container">
      <div class="menu" 
        :class="{'mobile-menu-opened': mobileMenuOpen}"
        @click.stop="mobileMenuOpen && toggleMobileMenu()"
      >
        <ul class="menu-items">
          <li class="item-active"><a href="#">HOME</a></li>
          <li class="item-inactive"><a href="#">WORK</a></li>
          <li class="item-inactive"><a href="#">ARTICLES</a></li>
          <li class="item-inactive"><a href="#">CONTACT</a></li>
        </ul>

        <div class="mobile-menu-icon">
          <font-awesome-layers class="fa-3x">
            <a href="#" @click.stop="toggleMobileMenu()">
              <font-awesome-icon :icon="activeMenuIcon != undefined ? activeMenuIcon : 'bars'"/>
            </a>
          </font-awesome-layers>
        </div>

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

export default Vue.extend({
  data() {
    return {
      mobileMenuOpen: false as boolean,
    }
  },
  methods: {
    toggleMobileMenu() {
      this.mobileMenuOpen = !this.mobileMenuOpen
    }
  },
  computed: {
    activeMenuIcon(): string {
      return this.mobileMenuOpen ? 'times' : 'bars'
    }
  },
})
</script>

<style lang="scss">

.menu {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 3rem;

  .horizontal-divider {
    width: 90%;
    border-bottom: 4px solid $color_primary_darker;
  }

  .menu-items {
    display: flex;
    width: 100%;
    justify-content: space-between;
    padding: 0;
    //margin: 0 0 clamp(0.25em, 1em, 2em) 0;
   
    :last-child {
      margin-right: 0;
    }

    li {
      //row-gap: 1em;
      //margin-right: 1em;
      //flex-grow: 1;
      list-style-type: none;
      border-radius: 4px;
      box-shadow: 6px 6px 4px rgba($color: $color_black, $alpha: 0.25);

      &:hover {
        cursor: pointer;
      }

      a {
        font-family: Overpass;
        font-size: 3vw;
        font-weight: 800;

        padding: 1vh 3vw 0 3vw;

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

  .mobile-menu-icon {
    visibility: hidden;

    a {
      color: $color_white;
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

  border-width: clamp(1em, 2em, 4em);
  border-style: solid;
  border-color: $color_primary_darker;
}

.page-container {
  display: flex;
  flex-direction: column;  

  height: 100%;
  //padding: 1.75rem 2rem;

  color: $color_white;
  // border: 4px solid $color_white;
}

@media (max-width: $breakpoint-phone) {
  .menu {
    display: flex;
    flex-direction: column;

    // Show menu icon, if mobile breakpoint was hit
    .mobile-menu-icon {
      visibility: visible;
    }
  
    .menu-items {
      position: absolute;
      top: -100px;
    }
    
    .horizontal-divider {
      display: none;
    }
  }

  .mobile-menu-opened {
    overflow: hidden;
    position: absolute;
    width: 100vw;
    height: 100vh;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    opacity: 1;
    background-color: rgba(0,0,0,0.5);
    transition: 0.33s ease-in-out;
    z-index: 2;

    .menu-items {
      position: static;

      display: flex;
      flex-direction: column;

      .item-active, .item-inactive {
        padding: 1.25em;
        border-radius: 0;
        text-align: center;

        margin-bottom: 1em;
      }

      :last-child {
        margin-bottom: 0;
      }
    }

    .mobile-menu-icon {
      visibility: visible;
    }
  }
  .mobile-menu-closed {
    visibility: hidden;

    .menu-items {
        top: -100px;
        z-index: 0;
        display: flex;
    }
  }

  .home-card {
    flex-direction: row-reverse;
    padding-bottom: 20vh;

    .face {
      display: none; // temporary. 
      padding-top: 2em;
      padding-right: 0;

      img {
        max-height: 25vh;
        max-width: 50vw;
      }
    }

    .greeting {
      padding-left: 0;

      h1, h2 {
        font-size: 6em;
      }
    }
  }
}

</style>
