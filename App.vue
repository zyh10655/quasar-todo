<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h2>Welcome to vue</h2>
  <div>Please select ur ideal</div>
  <div>
    <button 
    v-for="(item,index) in data.foods" 
    v-bind:key="index"
    @click="data.selectedFoodWay(index)"
    >
      {{index}}:{{item}}
    </button>
  </div>
  <div>Your choice:[{{data.selectedFood}}]</div>
</template>

<script lang="ts">
import { defineComponent ,ref ,reactive} from 'vue';
interface DataProps{
  foods: string[];
  selectedFood: string;
  selectedFoodWay: (index: number) => void;
}


export default{
  name: 'App',
  setup(){
    const data: DataProps = reactive({
      foods:["coffee","hotdog","pine"],
      selectedFood:"",
      selectedFoodWay:(index: number)=>{
        data.selectedFood=data.foods[index];
      },
    });

    // const foods = ref(["coffee","hotdog","pine"]);
    // const selectedFood = ref("");
    // const selectedFoodWay =(index: number)=>{
    //   selectedFood.value=foods.value[index];
    // };
    return{
      data,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
