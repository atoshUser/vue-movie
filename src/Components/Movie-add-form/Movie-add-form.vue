<template >
    <form class="movie-add-box">
          <input type="text" placeholder="Qanday kino?" autocomplete="off">
          <input type="text" placeholder="Nechi marotaba ko'rilgan" autocomplete="off" >
          <button class="add" type="submit">Qo'shish</button>
    </form>
</template>
<script>
export default {
    
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