<template>
    <div v-if="movies.length< 1" class="warn">Ma'lumotlar mavjud emas</div>
   <ul v-else  class="movie-list">
      <MovieItem v-for="movie in movies" :movie = "movie" @clearState="$emit('clearState',movie.id)" @onLike="this.$emit('onChangeState',movie.id)"/>
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

 .warn{
    display: flex;
    font-size: 30px;
    font-weight: 500;
    margin: 100px 0;
    justify-content: center;
 }
</style>