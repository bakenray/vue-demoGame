<template>
  <div class="cell" @click="clickEvent"> 
     <div v-if="isX">{{text}}</div> 
     <div v-else></div> 
  </div>
</template>
<script>
export default {
    props:{
        count:{
            type:Number,
            default:null
        }
    },
    data(){
        return{
            isX:false,
            text:''
        }
    },
    methods:{
        clickEvent(){
            if(this.text !== ""){return}
            this.isX = true
            this.text = this.count %2 === 0?"O":"X"
            this.$emit('click',this.text)
        }
    }
}
</script>
<style lang="scss">
    .cell{
        display: flex;
        justify-content: center;
        align-items: center;
        border:1px solid #ccc;
        width:100px;
        height:100px;
        font-size: 40px;
        font-weight: bold;
    }
@media(max-width:768px) {
    .cell{
        display: flex;
        justify-content: center;
        align-items: center;
        border:1px solid #ccc;
        width:30vw;
        height:30vw;
        font-size: 40px;
        font-weight: bold;
    }
}
</style>