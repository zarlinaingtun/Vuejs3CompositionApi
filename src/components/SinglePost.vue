<template>
  <h2>{{post.title}}</h2>
  <p>{{cutpostbody}}</p>
</template>

<script>
import { computed } from '@vue/reactivity'
export default {
props:['post'],
setup(props){
//    console.log(props.post);
let cutpostbody=computed(()=>{
    return props.post.body.substring(0,100)+'...';
})
return {cutpostbody};
}
}
</script>

<style>

</style>