<template>
  <div class="blok" v-if="showBlock" @click="krajMerenja">
      klikni me!
  </div>
</template>

<script>
export default {
    props: ['odlaganje'], 
    data() {
        return {
           showBlock: false,
           stoperica: null,
           vremeOdgovora: 0
        }

    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.pocetakMerenja()
        }, this.odlaganje) 
    },
    methods: {
        pocetakMerenja() {
            this.stoperica = setInterval(() => {
                this.vremeOdgovora += 10
                }, 10) 
        },
        krajMerenja(){
            clearInterval(this.stoperica) 
            this.$emit('kraj', this.vremeOdgovora)
        }
    }
}
</script>

<style>
  .blok {
      width: 400px;
      border-radius: 20px;
      background: #af0f6c;
      color: white;
      text-align: center;
      padding: 100px 0;
      margin: 40px auto;
}

</style>