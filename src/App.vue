<template>
  <div id="app">
    <b-button variant="primary" v-if="showForm" @click="closeForm">Show Movies</b-button>
    <b-button variant="primary" v-else @click="openForm">Add Movie</b-button>
    <create-movie v-if="showForm"/>
    <movies-table v-else/>
    
  </div>
</template>

<script>
import MoviesTable from './components/MoviesTable.vue'
import CreateMovie from './components/CreateMovie.vue'

export default {
  name: 'App',
  components: {
    MoviesTable,
    CreateMovie
  },
  data(){
    return {
      showForm:false
    }
  },
  methods:{
    openForm(){
      this.showForm = true
    },
    closeForm(){
      this.showForm = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
