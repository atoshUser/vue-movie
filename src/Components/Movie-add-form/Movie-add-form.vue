<template >
    <form class="movie-add-box" @submit.prevent @submit="submitForm">
          <input type="text"  v-model="name" placeholder="Qanday kino?" autocomplete="off" >
          <input type="number" v-model="view"   placeholder="Nechi marotaba ko'rilgan" autocomplete="off" >
          <button class="add" type="submit">Qo'shish</button>
    </form>
</template>
<script>
export default {
     data(){
        return{
          name:'',
          view:null,
          isLiked:false
        }
     },
     methods:{
    
       submitForm(){
        const newMovie = {
            name:this.name,
            view:this.view,
            isLiked:this.isLiked
         }
         this.$emit("createObj",newMovie)  
          this.name = '',
          this.view = null
        
       }
    }
  

}
</script>
<style  scoped>
.movie-add-box{
    display: flex;
    justify-content: space-between;
}

    input, button{
        flex-grow: 1;
        padding: 5px;
        border-radius: 8px;
        outline: none;
        border: 1px solid #333;
    }
   input{
    padding: 0 0 0 15px;
   }
</style>