
<template>
    <div class="container wrapper" >
        <div class="app-heading">
        <span>Barcha ko'rilgan kinolar soni : {{ movies.length }}</span>
        <span>Sevimli kinolar soni : {{ movies.filter((item) => item.isLiked).length }}</span>
        </div>
          <div class="box-search-panel app-heading">
               <SearchPanel/>
                <AppFilter/>
          </div>
           <MovieList :movies="movies"/>
           <div class="movie-add">
                  <h2>Yangi kino qo'shish</h2>
                  <MovieAddForm  @createObj="addObjToList" />
           </div>
    </div>
</template>

<script>
    import SearchPanel from "@/Components/searchPanel/SearchPanel.vue"
    import AppFilter from "../AppFilter/AppFilter.vue";
    import MovieList from "../MovieList/MovieList.vue";
    import MovieAddForm from "../Movie-add-form/Movie-add-form.vue";
export default {

     components:{
    SearchPanel,
    AppFilter,
    MovieList,
    MovieAddForm
} ,

data(){
  return{
     movies:[ 
      {name:"Abdurahmon",view:580,isLiked:false},
      {name:"Anora",view:65,isLiked:true},
      {name:"Elon Mask",view:5000,isLiked:true},
      {name:"Selena Gomes",view:10000,isLiked:true}
      ]
  }
} ,
methods : {
  addObjToList(obj){
     this.movies.push(obj)
  }
}

}
</script>



<style>
 .wrapper{
    display: flex;
    flex-direction: column;
    height:  100vh;
    padding:50px;
 }

 .app-heading{
    display: flex;
    flex-direction: column;
    padding: 15px;
    background-color: aliceblue;
    margin-bottom: 20px;
    box-shadow: 2px 4px 12px 2px rgb(23, 20, 20);
    color:#222;
    font-size: 25px;
    font-weight: 500;
 }

 .box-search-panel{
   display: flex;
   flex-direction: column;
   gap: 20px;
   margin-bottom: 35px;
 }

.movie-add{
   padding: 15px;
   background-color: rgba(240, 255, 255, 0.736);
   color:#222
}
</style>