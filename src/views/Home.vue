<template>
  <h1>Home</h1>
  <h2>My name is {{name}}.Age is {{age}}</h2>

  <input type="text" v-model="name"/>
  <button @click="handleClick">Click</button>
  <button @click="age++">Increase Age</button>
  <hr>

  <h1>Person One</h1>
  <h2>{{personOne.name}}</h2>
  <button @click="changeOne">Change One</button>

  <hr>

  <h1>Person Two</h1>
  <h2>{{personTwo.name}}</h2>
  <button @click="changeTwo">Change Two</button>

  <hr>
  <p>City One-{{cityone}}</p>
  <button @click="cityOne">Click</button>

  <hr>
  <p>City Two-{{citytwo}}</p>
  <button @click="cityTwo">Click</button>

</template>

<script>
import { reactive, ref } from '@vue/reactivity';


export default {
  setup(){
    let name=ref('Zar Li');//reactive value
    let age=ref(21);
    console.log(name.value);

    let handleClick=()=>{
      name.value="Ma Ma";
    }
  
    // Person One
    //ref()
    let personOne=ref({name:'Kyaw',age:25});
    let changeOne=()=>{
      personOne.value.name="Change Kyaw";
    }
    
    // Person Two
    //reactive()
    let personTwo=reactive({name:'Su',age:26});
    let changeTwo=()=>{
      personTwo.name="Change Su";
    }
    
     //ref() can change all value to reactivity
    let cityone=ref("Mandalay");
    let cityOne=()=>{
      cityone.value="Yangon"
    }

    //reactive() can't change primitive value("Japan") to reactivity 
    //only array,object can change
    let citytwo=reactive("Japan");
    console.log(citytwo);
    let cityTwo=()=>{
      citytwo="Noway";
    }

     return {name,age,handleClick,personOne,changeOne,personTwo,changeTwo,cityone,cityOne,citytwo,changeTwo};
  }
  
}
</script>
