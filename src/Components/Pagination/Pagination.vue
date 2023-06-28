<template>
   <ul class="pagination-list">
     <li class="list-item" v-for="item in Total" @click="changeActiveBtn" :key="item" :class="{ 'active' :  activeBtn === item  }" >{{ item }}</li>
    
   </ul>
</template>
<script>
export default {
    props:{
        Total:{
            type:Number,
            required:true
        },
        page:{
            type:Function,
            required:true
        }
    },
    data(){
         return{
             activeBtn:1
         }
    },
    methods:{
         changeActiveBtn(e){
               this.activeBtn =  Number(e.target.textContent)
               this.page(this.activeBtn)
         }
    },
   
}

</script>
<style scoped>
    .pagination-list{
        display: flex;
        justify-content: center;
        background-color: #fff;
        color:#222;
        padding: 0;
        list-style: none;
        border: 1px solid #234;
    }
    .list-item{
        padding: 7px;
        cursor: pointer;
        border-left: 1px solid #234;
    }
    .list-item:first-child{
        border-left: none;
    }
    .active{
        background-color: rgba(25, 25, 218, 0.993);
        color:white
    }
</style>