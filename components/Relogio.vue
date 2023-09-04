
Peço desculpas pela confusão. Parece que a formatação dos minutos não está sendo aplicada corretamente. Vamos corrigir isso. Você pode usar a função String.padStart() para garantir que os minutos tenham sempre dois dígitos. Aqui está como fazer isso:

vue
Copy code
<template>
  <div class="Content-Relogio">
    <div class="card">{{ horas }}</div>
    <div class="card">{{ minutos }}</div>
    <div class="card">{{ segundos }}</div>
  </div>
</template>

<style>
.Content-Relogio {
  width: 840px;
  height: 50%;
  background-color: black;
  display: flex;
  flex-direction: row;
  gap: 80px;
  justify-content: center;
  align-items: center;
  border: 2px solid black;
  border-radius: 12px;
  background: linear-gradient(to bottom, #000000, #1a1a1a, #000000);
}
.card {
  width: 25%;
  height: 70%;
  background-color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 90px;
  
}


@media(max-width: 840px){

    .Content-Relogio{
        width: 100%;
        gap: 30px;
        margin: 30px;
    }
    .card {
        font-size: 30px;
        height:150px;
        
    }
}


@media(max-width: 420px){

.Content-Relogio{
  width: 100%;
}
.card {
 height: 100px;
width: 80px;
margin: 7px;
    
}
}

</style>

<script setup lang="ts">
import { ref} from 'vue';

const dataAtual = ref(new Date());
let horas = ref(dataAtual.value.getHours());
let minutos = ref(dataAtual.value.getMinutes().toString().padStart(2, '0'));
let segundos = ref(dataAtual.value.getSeconds().toString().padStart(2, '0'));

function atualizar() {
  const novaData = new Date();
  horas.value = novaData.getHours();
  minutos.value = novaData.getMinutes().toString().padStart(2, '0');
  segundos.value = novaData.getSeconds().toString().padStart(2, '0');
}

const intervalo = setInterval(atualizar, 1000);



</script>