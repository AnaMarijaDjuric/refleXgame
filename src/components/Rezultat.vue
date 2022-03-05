<template>
  <p>Brzina - {{ rezultat }} ms</p>
  <p class = "rang">{{ rang }}</p>
</template>
<script>
export default {
    props: ['rezultat'], 
    data(){
        return{
             rang: null
            }
     },
     mounted(){
        if(this.rezultat < 250) {
            this.rang = 'Refleksi brzine svetlosti!'
        } else if(this.rezultat < 400) {
            this.rang = 'Zadovoljavajući refleksi...'
        } else{
             this.rang = 'Pokušaj ponovo! Jako si spor'
            }
     }      
}
</script>

<style>
.rang {
    font-size: 1,4dem;
    color: #af0f6c;
    font-weight: bold;
}
</style>