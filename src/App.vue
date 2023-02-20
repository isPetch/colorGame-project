<script setup>
import {ref} from 'vue'
const score =ref(0)
const dsinone = ref(false)
const player=ref('')


//สุ่มสี
const colorss = [
{yes: "bg-red-500" ,no : "bg-red-400"}, 
{yes: "bg-green-500" ,no : "bg-green-400"},  
{yes: "bg-yellow-500" ,no : "bg-yellow-400"},  
{yes: "bg-pink-500" ,no : "bg-pink-400"}, 

{yes: "bg-amber-700" ,no : "bg-amber-600"}, 
{yes: "bg-red-800" ,no : "bg-red-700"}, 
{yes: "bg-orange-500" ,no : "bg-orange-400"}
]

let lucky = colorss[Math.floor(Math.random() * colorss.length)];
const randomColor1 =[]
const randomColor2 =[]
const randomColor3 =[]
const randomColor4 =[]

const functionRandom1=()=>{
  for (let i = 0; i < 4; i++) {
    if (randomColor1.length < 3) {
      randomColor1.push(lucky.yes)
    }else{
      randomColor1.push(lucky.no)
    }
  }
}
functionRandom1()

const functionRandom2=()=>{
  for (let i = 0; i < 9; i++) {
    if (randomColor2.length < 8) {
      randomColor2.push(lucky.yes)
    }else{
      randomColor2.push(lucky.no)
    }
  }
}
functionRandom2()

const functionRandom3=()=>{
  for (let i = 0; i < 16; i++) {
    if (randomColor3.length < 15) {
      randomColor3.push(lucky.yes)
    }else{
      randomColor3.push(lucky.no)
    }
  }
}
functionRandom3()

const functionRandom4=()=>{
  for (let i = 0; i < 25; i++) {
    if (randomColor4.length < 24) {
      randomColor4.push(lucky.yes)
    }else{
      randomColor4.push(lucky.no)
    }
  }
}
functionRandom4()

function shuffle(array) {
  let currentIndex = array.length,  randomIndex;

  while (currentIndex != 0) {
    randomIndex = Math.floor(Math.random() * currentIndex);
    currentIndex--;

    [array[currentIndex], array[randomIndex]] = [
      array[randomIndex], array[currentIndex]];
  }

  return array;
}
const randomPosition1 = shuffle(randomColor1)
const randomPosition2 = shuffle(randomColor2)
const randomPosition3 = shuffle(randomColor3)
const randomPosition4 = shuffle(randomColor4)

const changeColor1 = (randomPosition1) => {
  if (randomPosition1[randomPosition1.length] = lucky.no) {
    score.value++
  }
  lucky = colorss[Math.floor(Math.random() * colorss.length)]
  randomColor1.length = 0
  functionRandom1()
  randomPosition1 = shuffle(randomColor1)
}
const changeColor2 = (randomPosition2) => {
  if (randomPosition2[randomPosition2.length] = lucky.no) {
    score.value++
  }
  lucky = colorss[Math.floor(Math.random() * colorss.length)]
  randomColor2.length = 0
  functionRandom2()
  randomPosition2 = shuffle(randomColor2)
}
const changeColor3 = (randomPosition3) => {
  if (randomPosition3[randomPosition3.length] = lucky.no) {
    score.value++
  }
  lucky = colorss[Math.floor(Math.random() * colorss.length)]
  randomColor3.length = 0
  functionRandom3()
  randomPosition3 = shuffle(randomColor3)
}
const changeColor4 = (randomPosition4) => {
  if (randomPosition4[randomPosition4.length] = lucky.no) {
    score.value++
  }
  lucky = colorss[Math.floor(Math.random() * colorss.length)]
  randomColor4.length = 0
  functionRandom4()
  randomPosition4 = shuffle(randomColor4)
}




//countdows
let countdows 
let time = ref(60)
countdows = ref(setInterval(() => {

  if (time.value == 0) {
    clearInterval(countdows)
    return 
  } 
  time.value--
}, 1000))



</script>
 
<template>
<div class="w-screen h-screen " style="background-color: #2A303C">
  <div class="flex w-full h-full">
    <div class="w-full h-full" :class="dsinone ? 'none' : 'show'">
      <div class="flex w-full h-2/6 justify-center">
        <img src="./assets/gameLogo.png" >
      </div>
      <div class="flex w-full h-1/2">
        <div class="flex w-2/6 h-full  m-auto rounded-xl" style="background-color: #334155">
          <div class="flex flex-col w-5/6 h-full  m-auto ">
            <div class="flex w-full h-2/3  border-b-2 border-gray-500">
              <div class="flex flex-col w-1/2 h-2/3 m-auto pt-6 space-y-4">
                <input type="text" placeholder="Type your name..." class="input input-bordered w-full max-w-xs " v-model="player"/>
                <button  class=" btn w-full normal-case" style="background-color: #111B2E" @click="dsinone = !dsinone , time = 60" >Let's start!</button>
              </div>
            </div>
            <div class="w-full h-1/3 ">
              <div class="flex flex-col w-1/2 h-2/3 m-auto pt-8">
                
                <label for="my-modal" class=" btn w-full normal-case" style="background-color: #111B2E">How to play</label>
                <input type="checkbox" id="my-modal" class="modal-toggle" />
                <div class="modal">
                  <div class="modal-box text-white" style="background-color: #304477">
                    <h2 class="font-bold text-xl text-center">How to play</h2>
                    <p class="py-4">Click on the different shade of color in a short period of time. Once you find the different shade, you click it and score one point if it is the different one.</p>
                    <div class="modal-action justify-center">
                      <label for="my-modal" class="btn " style="background-color: #6A88B2" >OK</label>
                    </div>
                  </div>
                </div>

              </div>
            </div>
          </div>

        </div>
      </div>
    </div>


    <div class="w-full h-full" :class="dsinone ? 'show' : 'none'">
      <div class="flex w-full h-1/6 justify-start ">
        <div class="flex h-2/6 ml-4 "><img src="./assets/gameLogo.png"  ></div>
      </div>
      
      <div class="flex w-full h-3/5 "  v-if="time != 0">
        <div class="flex w-1/3 h-full justify-end">
          <div class="flex flex-col w-2/5 h-full text-white space-y-2">
            <div class="flex items-center space-x-2">
              <div class="font-bold">Player:</div>
              <div v-if="player.length === 0 ">Guest </div>
              <div v-else>{{ player }}</div>
            </div>
            <div class="flex items-center space-x-2">
              <div class="font-bold">Score:</div>
              <div>{{ score }}</div>
            </div>  
          </div>
        </div>
        <div class="flex w-2/3 h-full">
          <div class="flex w-1/2 h-full">
            <div class="flex w-5/6 h-full m-auto rounded-xl flex-col" style="background-color: #334155">
              <div class="flex w-full h-1/5  mt-2">
                    <div class="font-mono text-6xl m-auto text-white">
                      <p>{{ time }}</p>
                    </div>
              </div>


              <div class="flex w-full h-5/6  m-auto ">
                <div class="flex w-56 h-56 space-x-1  m-auto " v-if="score >= 0 && score <=4">
                  <div class="grid grid-cols-2 gap-1 m-auto" >
                    <div v-for="random in randomPosition1" class="flex w-full h-full " @click="changeColor1(randomPosition1) ">
                      <div class="rounded-full w-28 h-28" :class="random" > </div>                      
                    </div>
                  </div>
                </div>  
                <div class="flex w-72 h-72 space-x-1  m-auto "  v-if="score >= 5 && score <=14">
                  <div class="grid grid-cols-3 gap-1 m-auto" >
                    <div v-for="random in randomPosition2" class="flex w-full h-full " @click="changeColor2(randomPosition2) ">
                      <div class="rounded-full w-24 h-24" :class="random" > </div>                      
                    </div>
                  </div>
                </div> 
                <div class="flex w-72 h-72 space-x-1  m-auto "  v-if="score >= 15 && score <=24">
                  <div class="grid grid-cols-4 gap-1 m-auto" >
                    <div v-for="random in randomPosition3" class="flex w-full h-full " @click="changeColor3(randomPosition3) ">
                      <div class="rounded-full w-16 h-16" :class="random" > </div>                      
                    </div>
                  </div>
                </div> 
                <div class="flex w-80 h-80 space-x-1  m-auto "  v-if="score >= 25 ">
                  <div class="grid grid-cols-5 gap-1 m-auto" >
                    <div v-for="random in randomPosition4" class="flex w-full h-full " @click="changeColor4(randomPosition4) ">
                      <div class="rounded-full w-14 h-14" :class="random" > </div>                      
                    </div>
                  </div>
                </div> 
              </div>


            </div>
          </div>
        </div>
      </div>
      <div class="flex w-full h-1/6  justify-center"  v-if="time != 0">
        <div class="flex w-1/4 h-full  items-center justify-center space-x-4">
          <button class=" btn w-2/5 capitalize" style="background-color: #AC9C48"  @click="dsinone = !dsinone , score=0 " >Main menu</button>
          <button class=" btn w-2/5 capitalize" style="background-color: #AC9C48"  @click="score=0, time = 60" >Restart Game</button>
        </div>
      </div>

      <div class="flex w-full h-4/6  justify-center" v-else="time = 0">
        <div class="flex flex-col w-1/3 h-full ">
          <div class="flex  w-full h-5/6 rounded-xl " style="background-color: #334155">
            <div class="flex flex-col w-4/6 h-4/6  m-auto items-center justify-center space-y-6">
              <p class="text-4xl" style="color : #FFDA1B" >Congratulations!</p>
              <p class="text-4xl text-white" v-if="player.length === 0 ">Guest</p>
              <p class="text-4xl text-white" v-else>{{ player }}</p>
              <p class="text-4xl text-white">{{ score }} point</p>
            </div>
          </div>
          <div class="flex w-full h-1/6  items-center justify-center space-x-4">
            <button class=" btn w-2/5 capitalize" style="background-color: #AC9C48"  @click="dsinone = !dsinone , score=0" >Main menu</button>
          <button class=" btn w-2/5 capitalize" style="background-color: #AC9C48"  @click="score=0, time = 60" >Restart Game</button>
          </div>
        </div>
      </div>
      

    </div>


  </div>

</div>
</template>
 
<style scoped>
.none {
  display: none;
}
.show {
  display: block;
}


</style>