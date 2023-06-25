<template>
   <ul class="movie-list">
      <MovieItem/>
      <MovieItem/>    
   </ul>
</template>


<script>
  import MovieItem from '../MovieItem/MovieItem.vue';
export default {
    components: { MovieItem }
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