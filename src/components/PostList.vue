<template>
  <div v-for="post in posts" :key="post.id">
      <SinglePost :post="post"></SinglePost>
  </div>
</template>

<script>
import { onMounted, onUnmounted, onUpdated } from '@vue/runtime-core';
import SinglePost from './SinglePost'
export default {
components: { SinglePost },
props:['posts'],
setup(props){
    console.log(props.posts);
    //Lifecircle Hook
    onMounted(()=>{console.log("Mounted")});
    onUnmounted(()=>console.log("Unmounted"));
    onUpdated(()=>console.log("Updated"));
  
}
}
</script>

<style>

</style>