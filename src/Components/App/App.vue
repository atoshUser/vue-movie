
<template>
    <div class="container wrapper" >
        <div class="app-heading">
        <span>Barcha ko'rilgan kinolar soni : {{ movies.length }}</span>
        <span>Sevimli kinolar soni : {{ movies.filter((item) => item.isLiked).length }}</span>
        </div>
          <div class="box-search-panel app-heading">
               <SearchPanel :updateState="updateHandler" />
                <AppFilter  :filterState="filterState" />
          </div>
           <MovieList :movies="filterList(showData(this.movies,this.data), this.filter)" :key="movies.id" @clearState="clearHandle" @onChangeState="changeStateLiked"/>
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
      
      ],
     data:'',
     filter:''
  }
} ,
methods : {
  addObjToList(obj){
     this.movies.push(obj)
  },

  changeStateLiked(id){
      this.movies.map((obj) => {
        if (id === obj.id) {
           return  obj.isLiked = !obj.isLiked
        }else {
        return obj
        }
      })
  },

  clearHandle(id){
    this.movies = this.movies.filter((item) => (item.id !== id))
  },

    showData(arr,text){
      console.log(text);
    if(!text.length){
      return   this.movies
    }else {
      return  arr.filter((item) => item.name.toLowerCase().includes(text.toLowerCase()))
    }
    },

  // UpdateStateHandler
   updateHandler(text){
      this.data = text
   },
   // FILTER lIST
   filterList(arr,filter){
      switch(filter){
         case  "mostView" : 
         return arr.filter((item) => item.view > 500);
         case "popular" : 
         return arr.filter((item) => item.isLiked);
         default : 
         return arr
      }
   },
    // change filter state
  filterState(text){
    this.filter = text
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