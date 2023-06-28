<template >
    <li class="movie-item">
       <div>
        <span>{{ movie.name }}</span>
        <span class="view">
             <span class="fa-solid fa-eye"></span>
            {{ movie.view }}</span>
       </div>
         <div class="box-btn" >
             <button @click="$emit('clearState',this.movie.id)" > <i  class="fa-solid fa-trash"></i></button>
             <button >
                 <span    v-if="movie.isLiked" @click="onClick">
                    <i class="fa-solid fa-heart"></i>
                  </span>
                  <span v-else  @click="onClick" >
                    <i class="fa-solid fa-thumbs-up finger"></i>
                  </span>
             </button>
            
         </div>
    </li>
</template>

<script>
export default {
    props:{
        movie: {
            type:Object,
            required:true,
        }
    },
    methods:{
        onClick(){
        this.$emit('onLike',this.movie.id)
       }
    },

    unmounted() {
        console.log('Unmount ishga tushdi')
    },
}
</script>

<style scoped>
    .movie-item{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 10px 0 10px 45px;
       background-color: aliceblue;
       color: #222;
       font-size: 22px;
       font-weight: 500;
padding: 7px 15px 7px 15px;
position: relative;
    overflow: hidden;
    }
    .movie-item:not(:last-child){
        border-bottom: 2px solid rgb(49, 59, 59);
    }
  
    .box-btn{
        display: flex;
        align-items: center;
       gap: 15px; 
    }
    .box-btn button{
        display: flex;
        border: none;
    }

     button:first-child{
        color: rgb(200, 181, 61);
     }
     button:nth-child(2){
        color: rgb(39, 72, 105);
     }
   button:last-child span:first-child{
       color:crimson
   }
   .finger{
    color:#345
   }
   .view{
     position: absolute;
     left: 55%;
   }
   
</style>