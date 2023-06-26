<template>
    <div>
        <input class="input" :value="inputData"  @input="addDataHandle"  type="text" placeholder="Kinolarni qidirish" autocomplete="off">
    </div>
</template>
<script>
export default {
     data(){
        return{
            inputData:''
        }
     },
    props:{
        updateState:{
            type:Function,
            required:true
        }
    },
    methods:{
        addDataHandle(e){
             this.inputData = e.target.value
             this.updateState(this.inputData)
        }
    }
}
</script>
<style scoped>
    .input{
        padding: 7px;
        width: 100%;
        outline: none;
        border-radius: 15px;
        border: 1px solid grey;
    }
    .input:active{
        outline: 3px solid rgba(0, 0, 255, 0.642);
    }
</style>