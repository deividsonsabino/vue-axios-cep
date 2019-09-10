<template>
  <div id="app">

    <search-cep-component>
    </search-cep-component>
    
  </div>
</template>

<script>
import SearchCepComponent from './components/SearchCepComponent'
export default {
  name: 'app',
  data () {
    return {
    
    }
  },
  components: {
    SearchCepComponent
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
