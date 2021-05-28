<template>
  <div class="page">
    <div class="page-container">
      
      <Menu />

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

</script>

<style lang="scss">

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