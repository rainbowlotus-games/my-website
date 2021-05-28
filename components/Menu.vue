<template>
  <div>
    <div :class="{'menu-overlay' : mobileMenuOpen}" @click.stop="mobileMenuOpen && toggleMobileMenu()"></div>
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
            <button @click.stop="toggleMobileMenu()">
              <font-awesome-icon :icon="activeMenuIcon != undefined ? activeMenuIcon : 'bars'"/>
            </button>
          </font-awesome-layers>
        </li>
      </ul>
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
  watch: {
    mobileMenuOpen: function() {
      console.log("mobileMenuOpen")

      if(this.mobileMenuOpen){
        document.documentElement.style.overflow = 'hidden'
        return
      }

      document.documentElement.style.overflow = 'auto'
    }
  }
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

  button {
    color: $color_white;
  }
}

// Small phones in landscape need bigger buttons / or maybe also the dropdown menu?
@media (min-width: $breakpoint-phone) and (max-width: $breakpoint-tablet) and (orientation: landscape) {
  * {
    background: green;
  }
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
        position: fixed;
        top: 0;
        right: 0;
        z-index: 2;

        button {
          border: 0;
          padding: 0;
          height: 100%;
          width: 100%;
          background: transparent;
          font-size: 100%;
          font-family: inherit;
          cursor: pointer;
          color: $color_white;
        }
      }
    }
    
    .horizontal-divider {
      display: none;
    }
  }

// Styling for when the menu is opened
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
}



@media (min-width: $breakpoint-tablet) {
  .menu {
    min-height: 3em;

    .menu-items {
      padding: 0;
      margin: 0;
      min-height: 3em; // min-height: 3em

      .item-active, .item-inactive {
        flex: 1;
        margin-right: 1em;

        a {
          display: block;
          width: 100%;
          text-align: center;
        }
      }

      :nth-last-child(2) {
        margin-right: 0;
      }
    }
  }
}

</style>
