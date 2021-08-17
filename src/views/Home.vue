<template>
  <h1>Home</h1>
  <h2>My name is {{name}}.Age is {{age}}</h2>

  <input type="text" v-model="name"/>
  <button @click="handleClick">Click</button>
  <button @click="age++">Increase Age</button>
</template>

<script>
import { ref } from '@vue/reactivity';


export default {
  setup(){
    let name=ref('Zar Li');
    let age=ref(21);
    console.log(name.value);

    let handleClick=()=>{
      name.value="Ma Ma";
    }
    return {name,age,handleClick};
  }
  
}
</script>
