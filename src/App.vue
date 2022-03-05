<template>
<h1>r e f l e X g a m e</h1>
<p>Da li si se ikada zapitao kakvi su tvoji refleksi?</p>
<p>Ako je tvoj odgovor DA, ovo je prava igrica za tebe! Potrudi se da što brže klikneš na blok i proveri koliko su brzi tvoji refleksi!</p>
<button @click="pocetak" :disabled="igra">Započni</button>
<Blok v-if="igra" :odlaganje="odlaganje" @kraj="krajIgre"/>
<Rezultat v-if="prikazivanjeRezultata" :rezultat="rezultat" />

</template>

<script>
import Blok from './components/Blok.vue'
import Rezultat from './components/Rezultat.vue'

export default {
  name: 'App',
  components: { Blok, Rezultat }, 
  data(){
    return {
      igra: false,
      odlaganje: null,
      rezultat: null,
      prikazivanjeRezultata: false
      }
    },
  methods: {
    pocetak() {
      this.odlaganje = 2000 + Math.random() * 5000 
      this.igra = true
      this.prikazivanjeRezultata = false
    },
    krajIgre(vremeOdgovora) { 
      this.rezultat = vremeOdgovora
      this.igra = false
      this.prikazivanjeRezultata = true
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  background: #af0f6c;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  }
  button[disabled]{
    opacity: 0.2;
    cursor: not-allowed;
  }

</style>
