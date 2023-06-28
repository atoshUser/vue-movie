
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
           <div  v-if="this.loading" class="warn">Ma'lumotlar hozirda mavjud emas</div>
           <MovieList v-else  :movies="filterList(showData(this.movies,this.data), this.filter)" 
           :key="movies.id" @clearState="clearHandle" @onChangeState="changeStateLiked"/>
            <Pagination :Total="totalPage" :page="changePage"/>
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
    import Pagination from "@/Components/Pagination/Pagination.vue"
import axios from "axios";
 import {v4 as uuidv4} from "uuid"
export default {
   components:{
    SearchPanel,
    AppFilter,
    MovieList,
    MovieAddForm,
    Pagination
} ,

data(){
  return{
     movies:[ 
      
      ],
     data:'',
     filter:'',
     loading:true,
     limit:5,
     page:1,
     totalPage:0
  }
} ,
methods : {

  async addObjToList(obj){
    try {
      const response  = await axios.post(`https://jsonplaceholder.typicode.com/users`,obj)
      this.movies.push(response.data)
        console.log(response);
      //this.movies.push()
    } catch (error) {
       alert(error.message)
    }
     
    //  this.movies.push(obj)
  },

  changePage(num) {
     console.log(num);
     this.page = num
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

  async clearHandle(id){
     try {
       await axios.delete(`https://jsonplaceholder.typicode.com/users/${id}`)
      this.movies = this.movies.filter((item) => (item.id !== id))
     } catch (error) {
      alert(error.message)
     }
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
  },
  mountLog(){
    console.log('Mount ishga tushdi');
  },
  updateLog(){
  console.log('Update ishga tushdi');
  },
  unMountLog(){
    console.log('Unmounted is working');
  },
   
  
  async  fetchApi(){
     try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users',{
           params:{
            _limit:this.limit,
            _page:this.page
          }
        })
         console.log(response);
            const newData = response.data.map((obj) => {
               return {
                 name:obj.name,
                view:obj.id * 125,
                id:uuidv4()
               }
            })
         this.totalPage = Math.ceil(response.headers['x-total-count'] / this.limit)
         this.movies = newData
     } catch (error) {
        console.log(error.message);
     }finally{
       this.loading = false
     }
  },
 
   improveTitle(text){
     if (text.length > 15) {
       return text.slice(15)
     }else {
      return text
     }
   }
  
},
 watch:{
     page(){
       this.fetchApi()
     }
 },

  mounted(){
    this.mountLog()
    this.fetchApi()
  },


   updated(){
     this.updateLog()
  },
  unmounted(){
this.unMountLog()
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

 /* here loading style   */  

 .warn{
    display: flex;
    font-size: 30px;
    font-weight: 500;
    margin: 100px 0;
    justify-content: center;
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