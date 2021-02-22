<template>
<br><br>
    <h3 style="color:light-blue">Current time taken : {{p_time}} ms <br> <span id="result">{{result}}</span> </h3>
    
</template>

<script>
export default {
    props: ['p_time'],
    data() {
        return {
             result: "null",
          
        }
    },
    mounted() {
            
                if(this.p_time <=260){
                    this.result = 'Great'
                }
                else if( this.p_time <= 350){
                    this.result = 'Good'
                } else if( this.p_time <= 400){
                    this.result = 'Average'
                }else
                   this.result = 'Bad'
                   
                  
            },
    methods: {
            
    },
    
}
</script>
<style >
#result{
    color: orangered;
    font-weight: bold;
    font-size: 20px;
    margin-top: 33px;
    display: block;
}

    
</style>