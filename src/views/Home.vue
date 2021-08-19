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

  <hr>
  <p>Computed Property</p>
  <p>Search Data {{search}}</p>
  <input type="text" v-model="search"/>
  <div v-for="username in filterusernames" :key="username">
    <p>{{username}}</p>
  </div>

<!-- PostList -->
<div  v-if="showPostList">
  <PostList :posts="posts"></PostList>
</div>
<button @click="showPostList=!showPostList">Show&Hide</button>
<button @click="posts.pop()">Delete One Post</button>
</template>

<script>
import PostList from '../components/PostList'
import { computed, reactive, ref } from '@vue/reactivity';


export default {
  components: { PostList },
  setup(){
    let showPostList=ref(true);
    let posts=ref([
    {title:'Project Title 1',body:" Lorem ipsum, dolor sit amet consectetur adipisicing elit. Modi saepe iste cumque ratione quas. Aspernatur, molestiae repudiandae corporis eveniet fugiat non nihil consectetur similique ab animi commodi eos aliquid cupiditate in dolorem magnam? Dolor asperiores deserunt dignissimos esse unde laudantium nesciunt, delectus et ullam placeat repellendus ipsum consequuntur nihil praesentium cumque quis ut perferendis? Fugit ut expedita illo nesciunt iste impedit ipsum itaque, aperiam, rerum consequatur officia molestias maxime sunt possimus natus? Accusantium, eius, id officia provident unde delectus repudiandae deleniti repellendus nemo possimus consectetur ullam cum beatae blanditiis aliquam quod natus esse quisquam obcaecati, illum earum. Nesciunt accusantium quos esse dolorem repudiandae facere? Perspiciatis delectus dolores aut sint eveniet fuga inventore possimus commodi. Ad necessitatibus harum molestias autem incidunt quis nam expedita recusandae sapiente. Soluta aperiam dolor est ipsum illo eos ex dolores tenetur, quia, et animi cum porro ad aut quis? Beatae vel quos et cupiditate nisi quam voluptatibus repellat rerum nobis dignissimos! Soluta incidunt labore autem perspiciatis delectus veniam est dolorum voluptatem in cum totam rerum animi nisi, sed velit ea cupiditate asperiores itaque nam eum quas iusto eligendi dignissimos? Deserunt esse laborum sapiente, et, nulla fugit possimus ipsam in facere eius minus suscipit, omnis nostrum amet!",id:1},
    {title:'Project Title 2',body:"Lorem Ispem",id:2}
    ]);

    let usernames=ref(["Mg Mg","Su Su","Aye Aye","Kyaw Kyaw","Aung"]);
    let search=ref('');
    
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
      // citytwo="Noway";
    }

    //Computed Property
    let filterusernames=computed(()=>{
      return usernames.value.filter(username=>{
        let smallusername=username.toLowerCase();
        let smallsearch=search.value.toLowerCase();
        return smallusername.includes(smallsearch);
      })
    })
     return {name,age,handleClick,personOne,changeOne,personTwo,changeTwo,cityone,cityOne,citytwo,changeTwo,usernames,search,filterusernames,posts,showPostList};
  }
  
}
</script>
