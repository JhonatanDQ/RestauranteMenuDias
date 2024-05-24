<script setup>
import { ref } from "vue";

const dias = ref(["Lunes", "Martes", "Miércoles", "Jueves", "Viernes"]);
const datos = ref(["tema 1", "tema 2", "tema 3", "tema 4"]);
const comida = ref(["Desayuno", "Almuerzo", "Cena"]);
const SelectedDinner = ref(["Arepa", "Pan"]);

const selectedIndex = ref(0);
const Selection = ref(true);

function isSelected() {
     Selection.value = !Selection.value;
}

function showInfo(i) {
  if (i == selectedIndex.value) {
    selectedIndex.value = -i
  } else {
    selectedIndex.value = i
  }
}

function cenaSeleccion(c) {
    console.log(c)
    SelectedDinner.value = ref(c)
}

</script>

<template>
  <div class="flex container max-w-[1500px] mx-auto justify-center mt-24">
    <h1 class="text-cyan-500 text-4xl underline uppercase mb-12">
      Restaurante universitario
    </h1>
  </div>

  <div class="flex justify-center mx-auto container items-center">
    <div class="grid grid-cols-1 space-y-5"
       
    >
      <div
      
        @click="showInfo(i)"
        v-for="(dia, i) in dias"
        key:i
        class="bg-slate-200 flex mx-auto h-[40px] w-[500px] p-1 justify-center ml-24 items-start select-none" 
        
        :class="{'bg-blue-200 text-white': selectedIndex == i}"
        >
        
        {{ dia }}


      </div>
    </div>

    <div class="flex container mx-auto max-w-[1600px] justify-center">
      <div class="bg-blue-200 flex container max-w-[500px] mx-auto justify-start p-2 ml-2 h-[280px] text-white">
        
        <h1
        @click="cenaSeleccion(c)" 
        v-for="(comidas, c) in comida" key:c
        class="text-white p-1 select-none"
        :class="{'text-black': SelectedDinner == c}"
        >
            {{ comidas }}
        </h1>

        <div class="bg-red-200"
        v-show="cenaSeleccion == 0"
        >
            {{ comida.value }}
        </div>

       
        
        {{ comida.value }}
      </div>
    </div>
  </div>
</template>
