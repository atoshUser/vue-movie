<template >
    <li class="movie-item">Ertugrul</li>
</template>

<script>
export default {
    
}
</script>

<style >
    .movie-item{
        display: flex;
        padding: 10px 0 10px 45px;
       background-color: aliceblue;
       color: #222;
       font-size: 22px;
       font-weight: 500;

    }
    .movie-item:not(:last-child){
        border-bottom: 2px solid rgb(49, 59, 59);
    }


</style>