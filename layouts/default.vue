<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
html {  
  font-family:
    'Chivo',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

html, body {
  height: 100vh;
  width: 100vw;
}

html {
/* Hide scrollbar for IE, Edge and Firefox */
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}
html::-webkit-scrollbar {
  display: none;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

</style>