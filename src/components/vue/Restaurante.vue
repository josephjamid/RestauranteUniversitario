<script setup>

import {ref} from 'vue'

const selectedIndex = ref (0)
const selectedFood = ref ('')
const foods = ref ([])
   

const dias = [
    {
        day : "lunes",
        menu:{
            desayuno: ["huevos","pan","arepa"],
            almuerzo: ["paella","carne asada","sancocho"],
            cena: ["huevos pericos","amburguesa","empanadas"]
        }
    },
    {
        day : "martes",
        menu:{
            desayuno: ["huevos","pan","arepa"],
            almuerzo: ["paella","pollo asado","carne en vistec"],
            cena: ["huevos turcos","empanada","caldo"]
        }
    },
    {
        day : "miercoles",
        menu:{
            desayuno: ["arepa","pan con cafe","empanada"],
            almuerzo: ["arroz con pollo","carne oreada","sancocho trifacico"],
            cena: ["arepa rellena","calentado","papa rellena"]
        }
    },
    {
        day : "jueves",
        menu:{
            desayuno: ["huevos","sandiwch","mazamorra"],
            almuerzo: ["frijoles","lentejas","sancocho"],
            cena: ["cafe con pan","amburguesa","empanadas"]
        }
    },
    {
        day : "viernes",
        menu:{
            desayuno: ["huevos revueltos"," pan con cholate","arepa rellena"],
            almuerzo: ["arroz de pollo ","carne asada","sancocho"],
            cena: ["huevos revueltos","arepa","empanadas"]
        }
    },
    {
        day : "sabado",
        menu:{
            desayuno: ["huevos","pan","arepa"],
            almuerzo: ["paella","carne asada","sancocho"],
            cena: ["huevos pericos","amburguesa","empanadas"]
        }
    },
    

]

function mostrar (i){
    if(i == selectedIndex.value){
        selectedIndex.value = -1

    }else{
        selectedIndex.value = i
    }

}

function showMenu(i){
    selectedFood.value = i
    foods.value = []
    const selectedMenu = dias[selectedIndex.value].menu[i]
    if(Array.isArray(selectedMenu)){

        selectedMenu.forEach(food => {foods.value.push(food)})

    }else{
        foods.value.push(selectedMenu)
    }
    
    



}
 



</script>

<template>
 <div class="  w-2/4 mx-auto flex mt-48  ">

  

    <div class="w-2/5">
        
        <div v-for="(dia, i) in dias" :key="i" class="bg-[#e0dfdd] mt-1" :class="{'bg-[#b8d6e0] ' :selectedIndex == i  } " >

            <h1 @click="mostrar(i)">{{ dia.day }}</h1>

        </div>
      
        
    </div>
    
        <div  class="bg-[#b8d6e0] w-3/5 mt-1">

            
         <div v-if="selectedIndex!== null">
            <div class="px-4 mx-12 mt-4 flex space-x-4 text-">
                <p @click="showMenu(i)"  v-for="(menu,i) in dias[selectedIndex].menu" class=" text-[#3b636e] hover:cursor-pointer hover:text-black" :class="{'text-[#3b636e] border-b border-black':selectedFood == i}"><strong>{{ i }}</strong> </p>
                
            </div>    
           <div class="mt-3">
                <div class="mt-3 flex items-center" v-for="(food,i) in foods">
                    <sapn class="inline-block w-2 h-2 bg-white rounded-full ml-4 "></sapn>
                    <p class="ml-10">{{ food }}</p>
                </div>
            </div>
        </div>

                
         </div>
    
</div>

</template>