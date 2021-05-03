<template>
  <div>

    <b-table
      id="my-table"
      :items="moviesProvider"
      :per-page="perPage"
      :current-page="currentPage"
      small
    ></b-table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'MoviesTable',
  data(){
    return{
      perPage: 1,
      currentPage: 1,
    }
  },
  computed: {
  },
  methods:{
    moviesProvider(ctx,callback){
      axios.get('http://localhost:2500/movie/movies')
        .then((res)=>{
          callback(res.data)
        })
        .catch(()=>{
          callback([])
        })
    }
  }
}
</script>

