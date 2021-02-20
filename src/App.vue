<template>
<div>
  <div class="main">
   <h1 style="color:orangered"> Reaction Game </h1>

    <button @click="play"  :disabled="isPlaying" >{{vari}}</button>

    <Block  :p_delay="delay" v-if="isPlaying"  @ended="endGame"  /> <!-- here p_delay is the props and by defining :p_delay we now can dynamically change the attribute value wich is stored in delay -->
     <Result  :p_time ="time" v-if="time != null" />  

  </div>
 <h3 style="color:light-blue;margin-top:200px" v-if="highestResult && (time != null)">Best time taken : <span style="color:#f44139">{{highestResult}} ms</span></h3> 

  </div>
</template>

<script>
import Block from './components/block.vue'
import Result from './components/result.vue'


export default {
  name: "App",
  components: {Block,Result},
  data() {
    return {
      isPlaying: false,
      delay: null,
      time:null,
      vari:"play",
      highestResult:null,
    };
  },
  methods: {
    play() {
      this.isPlaying = true;
      this.delay = Math.random() * 5000;
      this.time = null;
      this.vari = "disabled"
      console.log(this.delay)
    },
    high(score){
     
       if(this.highestResult == null ){
           this.highestResult = this.time
        
       }else if(this.highestResult > this.time){
            this.highestResult = this.time
          
       }
    },
    endGame(variable){
      this.time = variable;
      this.isPlaying = false;
        this.vari = "play"
        this.high(this.time)
    }
  },
  mounted(){
  
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #264653;
  margin-top: 60px;

}
*{
 background: #fffffc;
 color:#264653 ;
}
button{
  color: #61757e;
  text-decoration: none;
  padding: 5px 20px;
  background: #e9e8e8;
  border: 0px;
  cursor: pointer;
  font-weight:bold ;
  border-radius: 20px;
}
button:hover{
  background: #a2d2ff;
  color: #14213d;
}

</style>
