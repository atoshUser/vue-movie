<template>
    <div class="box-change-btn">
         <button  type="button" v-for="obj in filterButtons"   :key="obj.title"  @click="changeActiveButton(`${obj.activeBtn}`)" :class="{active : activeButton === `${obj.activeBtn}`}">{{ obj.title }}</button>
       
    </div>
</template>


<script>
export default {
    data(){
        return{
             activeButton:'all',
             filterButtons:[
                { activeBtn:'all',title:'Barcha kinolar'},
                { activeBtn:'popular',title:'Mashhur kinolar'},
                { activeBtn:'mostView',title:"Eng ko'p ko'rilgan kinolar"}
             ]
        }
    },
    props:{
       filterState : {
        type:Function,
        required:true
       }
    },
    methods:{
       changeActiveButton(prop){
          
           this.activeButton = prop;
           this.filterState(this.activeButton)
       },   
     
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