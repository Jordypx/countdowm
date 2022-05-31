<template>
<Count />
</template>

<script>
import Count from "./components/Count.vue";


export default {
  name: 'App',
  components: {
   Count
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Red+Hat+Text:wght@600;700&display=swap');



* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    text-decoration: none;
}


body {
    display: flex;
    justify-content: center;
    background: black;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    font-family: 'Red Hat Text', sans-serif;
}


</style>
