
<template>
    <div class="container wrapper" >
import AppFilter from "../AppFilter/AppFilter.vue";
        <div class="app-heading">
        <span>Barcha ko'rilgan kinolar soni : 3</span>
        <span>Sevimli kinolar soni : 0</span>
        </div>
          <div class="box-search-panel app-heading">
               <SearchPanel/>
                <AppFilter/>
          </div>
    </div>
</template>

<script>
    import SearchPanel from "@/Components/searchPanel/SearchPanel.vue"
    import AppFilter from "../AppFilter/AppFilter.vue";
export default {

     components:{
    SearchPanel,
    AppFilter
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
   margin-bottom: 15px;
 }
</style>