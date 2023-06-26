<template>
    <div class="box-change-btn">
         <button  type="button" @click="changeActiveButton('all')" :class="{active : activeButton === 'all'}">Barcha kinolar</button>
         <button type="button" @click="changeActiveButton('popular')" :class="{active  : activeButton === 'popular'}">Mashhur kinolar</button>
         <button type="button" @click="changeActiveButton('mostView')" :class="{active : activeButton === 'mostView'}">Eng ko'p ko'rilgan kinolar</button>
    </div>
</template>


<script>
export default {
    data(){
        return{
             activeButton:'all'
        }
    },
    methods:{
       changeActiveButton(prop){
           this.activeButton = prop
       }    
    }
}
</script>


<style>

.box-change-btn{
    display: flex;
}

.active{
    background-color: #234;
    color: white;
}

.box-change-btn button{
   padding: 5px;
   border: 1px solid #234;
   transition: background-color 0.5s ease, color 0.5s ease, 
    color 0.5s ease;
}





</style>