
<template >
    <form class="movie-add-box" @submit.prevent @submit="submitForm">

          <input type="text" ref="name"  v-model="name" placeholder="Qanday kino?" autocomplete="off" >
          <input type="number" v-model="view"   placeholder="Nechi marotaba ko'rilgan" autocomplete="off" >
          <PrimaryButton class="add" type="submit">Qo'shish</PrimaryButton>
    </form>
</template>
<script>
  import {v4 as uuidv4} from "uuid"
export default {
    data() {
        return {
            name: "",
            view: null,
            isLiked: false
        };
    },
    methods: {
        submitForm() {
           if (!this.name || this.view === null) {
             return []
           }
            const newMovie = {
                name: this.name,
                view: this.view,
                isLiked: this.isLiked,
                id: uuidv4()
            };
            this.$emit("createObj", newMovie);
            this.name = "",
                this.view = null;
            this.$refs.name.focus();
        },
    },
}
</script>
<style  scoped>
.movie-add-box{
    display: flex;
    justify-content: space-between;
}
  .add{
    color:white;
    background-color:#234;
    border: none;
    padding: 5px;
  }
    input{
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