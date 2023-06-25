<template>
    <div class="box-change-btn">
         <button type="button">Barcha kinolar</button>
         <button type="button">Mashhur kinolar</button>
         <button type="button">Eng ko'p ko'rilgan kinolar</button>
    </div>
</template>


<script>
export default {
    
}
</script>


<style>

.box-change-btn{
    display: flex;
}

.box-change-btn button{
   padding: 5px;
   border: 1px solid #222222bd;
   background-color: azure;
   transition: background-color 0.5s ease, 
    color 0.5s ease;
}

.box-change-btn button:hover{
    background-color: #234;
    color:white
}



</style>