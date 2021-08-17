<template>
  <h1>Home</h1>
  <h2>My name is {{name}}.Age is {{age}}</h2>
  <button @click="handleClick">Click</button>
</template>

<script>


export default {
  setup(){
    let name="Zar Li";
    let age=21;
    console.log(name);

    let handleClick=()=>{
      console.log('U click me');
    }
    return {name,age,handleClick};
  }
  
}
</script>
