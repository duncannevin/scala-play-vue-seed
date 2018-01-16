<template>
  <div class="vue-play">
    <nav>
      <a class="scala" href="https://www.scala-lang.org/">
        <img width="450" height="300"  :src="logos.scalaLogo" alt="Scala Logo" />
      </a>
      <a class="play" href="https://www.playframework.com/">
        <img width="400" height="400" :src="logos.playLogo" alt="Play Framework Logo" />
      </a>
      <a class="vue" href="https://vuejs.org/">
        <img class="App-logo" width="400" height="400" :src="logos.vueLogo" alt="Vue Logo" />
      </a>
    </nav>
    <div>
      <h2>Check out the project on GitHub for more information</h2>
      <h3>
        <a target="_blank" href="https://github.com/duncannevin/scala-play-vue-seed">
          scala-play-vue-seed
        </a>
      </h3>
      <h2>Project based on scala-play-react-seed by <a href="https://github.com/yohangz">Yohan Gomez</a></h2>
      <a target="_blank" href="https://github.com/yohangz/scala-play-react-seed">
        scala-play-react-seed
      </a>
    </div>
  </div>
</template>
<script>
  import assets from '../assets'
  export default {
    computed: {
      logos () {
        return assets
      }
    }
  }
</script>
