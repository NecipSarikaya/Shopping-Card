<template>
   <div class="progress">
      <div class="progress-bar bg-info" role="progressbar" :style="{width: width +'%'}" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
        {{counter}}/10
      </div>
    </div>
</template>


<script>
    import {eventBus} from "../main.js"
    export default {
        data() {
            return {
                counter : 0,
                width : 0
            }
        },
        created(){
            eventBus.$on("Progres" ,(length)=>{
                this.counter = length;
                this.width = length*10;
            })
        }
    }
</script>


<style>
    
</style>