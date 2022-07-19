<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click here <br>
    
    
  </div>
  
  

</template>

<script>
import { setDevtoolsHook } from '@vue/runtime-core';
export default {
    props:['timer'],
    data(){
        return{
            showBlock : false,
            score:0,
            stopWatch:null
        }
    },
    methods:{
        startTimer(){
            this.stopWatch=setInterval(()=>{
                this.score+=50;
                
            },50);
        },
        stopTimer(){
            clearInterval(this.stopWatch);
            this.$emit("endGame",this.score)
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock=true;
            this.startTimer()
        },this.timer)
    }
}
</script>

<style scoped>
    .block{
        width:400px;
        height: 300px;
        background: #71abab;
        margin: 50px auto;
        line-height:300px;
        border-radius: 20px;
        color:#ffffff;
        font-size: 30px;
    }
    
</style>