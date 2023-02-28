<script setup>
import HelloWorld from '../components/HelloWorld.vue'
</script>

<template>
  <div>
    <img src="https://ugb.edu.sv/observatorioverde/assets/img/UGBlogo.png"
            class="logo"
            height="150"
            width="450">
            
    <HelloWorld/>
    
    <p class="texto">Hector Alejandro Franco Berrios</p>
    <p class="texto">Geovanny Mauricio Alvarez</p>
    <p class="texto">David Arnoldo Hernandez Gomez</p>
    <p class="texto">Rene Ismael Fuentes Benitez</p>

  </div>
  
</template>

<style scoped>
.logo {
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #ff1635aa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #ec9b9baa);
}

.texto{
  font-family: Arial, Helvetica, sans-serif;
  font-size: 25px;
}
</style>
