<script setup>
import {ref } from "vue";

const moveLog = ref([]);
const playerHP = ref(10);
const monsterHP = ref(10);
const battleStatusMessage = ref('En curso ⚔️')

const getRandom = (max) => Math.floor(Math.random() * (max + 1));

const onMonsterDamage = (damage) => {
  if (damage >= monsterHP.value) {
    console.log('Ganaste');
    battleStatusMessage.value = 'Ganaste 🎉 🗣️'
    monsterHP.value = 0
    
  }
  else{
    moveLog.value.push(`Jugador 1 hizo ${damage} de daño.`);
    monsterHP.value -= damage;
    
  }
};
const onPlayerDamage = (damage) => {
  if (damage >= playerHP.value) {
    console.log('Perdiste');
    battleStatusMessage.value = 'Perdiste 🗿💀'
    playerHP.value=0
  }
  else{
    moveLog.value.push(`Monstruo hizo ${damage} de daño.`);
    playerHP.value -= damage;

  }
};

const onAttack = () => {
  let randomDamage = getRandom(3);
  console.clear();
  console.log("Daño generado por el jugador: " + randomDamage);
  onMonsterDamage(randomDamage);

  randomDamage = getRandom(3);

  console.log("Daño generado por el monstruo: " + randomDamage);
  onPlayerDamage(randomDamage);
};
const onSpecialAttack = () => {
  let randomDamage = getRandom(4);
  console.clear();
  console.log("Daño generado por el jugador: " + randomDamage);
  onMonsterDamage(randomDamage);

  randomDamage = getRandom(3);

  console.log("Daño generado por el monstruo: " + randomDamage);
  onPlayerDamage(randomDamage);
};
const onJump = () => {
  console.clear();
  console.log("Brincadoxd");
  moveLog.value.push("Se ha brincado. Sin efectos...");
};

</script>
<template>
  <div class="major-container">
    <header class="top-bar">
      <h1 class="text-black w-[100%] text-center text-3xl">Monster Slayer RPG</h1>
    </header>
    <main class="main-container py-[10%] px-[30%] space-y-2.5 overflow-auto">
      <section class="space-y-4">
        <div class="w-[100%] border rounded-xl border-black p-3 flex flex-col items-start bg-[#9A031E] text-2xl text-white">
          <h1>Vida del Monstruo</h1>
          <div class="life-gauge" :style="{ width: monsterHP + '%' }">
            <p>{{ monsterHP }}/100</p>
          </div>
        </div>
      </section>
      <section class="space-y-4">
        <div class="w-[100%] border rounded-xl border-black p-3 flex flex-col items-start bg-[#9A031E] text-2xl text-white">
          <h1>Tu Vida</h1>
          <div class="life-gauge" :style="{ width: playerHP + '%' }">
            <p>{{ playerHP }}/100</p>
          </div>
        </div>
      </section>
      <!-- sprites -->
      <section class="flex flex-row w-[100%] bg-[#FB8B24] justify-center space-x-25 border rounded-xl py-[5%]">
        <div ><img src="../public/assets/monster.png" class="w-[100px] h-[100px]" alt="no image"></img></div>
        <div><img src="../public/assets/roy_sprite.gif" class="w-[100px] h-[100px]" alt="no image"></img></div>
        <!-- <div><p>VS</p></div> -->
      </section>
      <section class="flex justify-center "><p class="text-center text-3xl">{{battleStatusMessage }}</p></section>
    </main>
    <!-- seccion de controles -->
    <footer class="bottom-bar">
      <!-- Atack controls -->
      <section class="flex flex-col justify-center w-[25%] overflow-auto">
        <div @click="onAttack" class="text-2xl text-white border border-white font-black align-middle cursor-crosshair">
          <h1 class="text-center">Atacar</h1>
        </div>
        <div @click="onSpecialAttack" class="text-2xl text-white border border-white font-black cursor-cell">
          <h1 class="text-center">Ataque especial</h1>
        </div>
        <div @click="onJump" class="text-2xl text-white border border-white font-black cursor-grab">
          <h1 class="text-center">Saltar</h1>
        </div>
      </section>
      <!-- Moves log -->
      <section class="flex flex-col overflow-y-auto w-[75%] text-xl text-white p-[1%]">
        <p v-if="moveLog.length === 0">No moves yet!</p>
        <p v-else v-for="move in moveLog">{{ move }}</p>
      </section>
    </footer>
  </div>
</template>

<style lang="css">
@import "tailwindcss";
.major-container {
  height: 76.9vh;
}
.top-bar {
  height: 8%;
  padding: 1%;
  /* background-color: oklch(0.82 0.2 75.14); */
  background-color: #E36414;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.main-container {
  height: 100%;
  background-color: #FB8B24;
  background: linear-gradient(#FB8B24, #E36414);
}
.life-gauge {
  padding: 1%;
  border-radius: 10px;
  background-color: #00c951;
  color: #000;
  transition: all 0.2s ease-in;
}
.bottom-bar {
  height: 22%;
  padding: 1%;
  display: flex;
  flex-direction: row;
  border-width: 3px;
  border-radius: 10px;
  border-color: azure;
  /* background-color: #0F4C5C; */
  background: linear-gradient(#1200a7, #0F4C5C);
}
</style>
