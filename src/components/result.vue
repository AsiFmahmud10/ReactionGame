<template>
<br><br>
    <h3 style="color:light-blue">Current time taken : {{p_time}} ms <br> {{result}} </h3>
    
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
            
                if(this.p_time < 260){
                    this.result = 'great'
                }
                else if( this.p_time < 350){
                    this.result = 'good'
                } else if( this.p_time < 400){
                    this.result = 'average'
                }else
                   this.result = 'bad'
                   
                  
            },
    methods: {
            
    },
    
}
</script>
<style >


    
</style>