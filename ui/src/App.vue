<template>
  <div class="App">
    <h1>{{ appSummary }}</h1>
    <vue-play></vue-play>
  </div>
</template>
<script>
  import VuePlay from './components/VuePlay.vue'
  export default {
    mounted () {
      this.getSummary(summary => this.appSummary = summary.content)
    },
    data () {
      return {
        appSummary: ''
      }
    },
    methods: {
      getSummary (cb) {
        return fetch(`/v1/summary`, {
          accept: "application/json"
        })
          .then(this.checkStatus)
          .then(this.parseJSON)
          .then(cb)
      },

      checkStatus (response) {
        if (response.status >= 200 && response.status < 300) {
          return response;
        }
        const error = new Error(`HTTP Error ${response.statusText}`);
        error.status = response.statusText;
        error.response = response;
        console.log(error); // eslint-disable-line no-console
        throw error;
      },

      parseJSON (response) {
        return response.json();
      }
    },
    components: {
      VuePlay
    }
  }
</script>
<style>
  body {
    margin: 0;
    padding: 0;
    font-family: sans-serif;
    background-color: rgb(39, 40, 34);
    color: #f0f8ff;
  }

  a {
    color: #00ffff;
  }

  .App {
    text-align: center;
  }

  .App-logo {
    animation: bounce 0.8s infinite alternate;
    -webkit-animation: bounce 0.8s infinite alternate;
  }

  @keyframes bounce {
    from {
      transform: translateY(35px);
    }
    to {
      transform: translateY(-25px);
    }
  }
  @-webkit-keyframes bounce {
    from {
      transform: translateY(35px);
    }
    to {
      transform: translateY(-25px);
    }
  }
</style>
