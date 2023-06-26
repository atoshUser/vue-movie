<template>
   <ul class="movie-list">
      <MovieItem v-for="movie in movies" :movie = "movie"/>
   </ul>
</template>


<script>
  import MovieItem from '../MovieItem/MovieItem.vue';
export default {
    components: { MovieItem },
 
    props:{
        movies:{
            type:Array,
            required:true,
        }
    }
}
</script>


<style>
    .movie-list{
        display: flex;
        flex-direction: column;
        background-color: antiquewhite;
        padding: 0;
        margin: 0 0 15px;
        box-shadow:3px 5px 7px #222;
    }

</style>