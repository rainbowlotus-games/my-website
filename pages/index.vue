<template>
  <div class="page">
    <div class="page-container">
      <div v-if="mobileMenuOpen" class="menu-overlay" @click.stop="mobileMenuOpen && toggleMobileMenu()"></div>
      <div class="menu" 
        :class="{'mobile-menu-opened': mobileMenuOpen}"
        @click.stop="mobileMenuOpen && toggleMobileMenu()"
      >
        <ul class="menu-items">
          <li class="item-active"><a href="#">HOME</a></li>
          <li class="item-inactive"><a href="#">WORK</a></li>
          <li class="item-inactive"><a href="#">ARTICLES</a></li>
          <li class="item-inactive"><a href="#">CONTACT</a></li>
          <li class="mobile-menu-icon">
            <font-awesome-layers class="fa-3x">
              <a href="#" @click.stop="toggleMobileMenu()">
                <font-awesome-icon :icon="activeMenuIcon != undefined ? activeMenuIcon : 'bars'"/>
              </a>
            </font-awesome-layers>
          </li>
        </ul>
        <div class="horizontal-divider"></div>
      </div>

      <div class="home-card">
        <div class="face">
          <img src="svg/face.svg" alt="SVG of my face">
        </div>
        <!-- <div class="vertical-divider"></div> -->
        <div class="greeting">
          <div class="hello">
            <h1>Hello,</h1>
            <h2>I'm Paul</h2>
          </div>
          <div class="title">
            <h3>web designer & student</h3>
          </div>
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

    .item-active, .item-inactive {
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
}

.mobile-menu-icon {
  display: none;

  a {
    color: $color_white;
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

    .hello {
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

    .title {
      h3 {
        padding: 0.125em 0.25em 0.125em 0.25em;
        font-family: Chivo;
        font-weight: 400;
        font-size: 2.75em;
        letter-spacing: 0.125em;
        background-color: $color_signal_alt;
      }
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
  border-color: $color_primary;
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
  .menu-overlay {
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
    transition: all 0.33s ease-in-out;
    z-index: 1;
    margin-top: 0;    
    padding-top: 0;
  }

  .menu {
    position: fixed; // would otherwise make rest of page move up once menu is opened
    width: 100%;

    display: flex;
    flex-direction: column;
  
    .menu-items {
      position: absolute;
      top: -200px;

      .item-active , .item-inactive {
        opacity: 0;
      }

      .mobile-menu-icon {
        position: relative;
        top: 200px;
        z-index: 2;
      }
    }
    
    .horizontal-divider {
      display: none;
    }
  }

  .mobile-menu-opened {
    z-index: 2;

    .menu-items {
      position: relative;
      top: 0;
      display: flex;
      flex-direction: column;
      transition: all 0.33s ease-in-out;

      .item-active, .item-inactive {
        display: inline-block;
        opacity: 1;
        padding: 0;
        border-radius: 0;
        text-align: center;

        a {
          display: block;
          padding: 2.125em 1em 2.125em 1em;
          font-size: 1em;
        }
      }

      .mobile-menu-icon {
        justify-content: center;
        margin-top: 1em;
        position: static;
        z-index: 2;
      }

      :last-child {
        border-bottom: none;
      }
    }
  }

  .mobile-menu-icon {
    display: flex;
    //transition: all 0.33s linear;
    box-shadow: none;
  }

  .home-card {
    flex: 0;
    flex-direction: row-reverse;
    margin-top: 12vh;

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
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;

      .hello {
        h1, h2 {
          font-size: 5em;
          text-align: left;
        }

        h2 {
          // Necessary because of font
          // having a slight offset to the right
          margin-right: 2vw;        
          margin-bottom: -2vh;
        }
      }

      .title {
        width: 100%;
        h3 {
          font-size: 2em;
          text-align: center;
        }
      }
    }
  }

  .page {
    border: none;
  }

  .page-container {
    //position: fixed;
  }
  
  .arrow-down {
    margin-top: auto;
    padding-bottom: 2vh;
  }
}

</style>
