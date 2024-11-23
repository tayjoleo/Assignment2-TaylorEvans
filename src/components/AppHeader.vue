<template>
  <header>
    <h1>TASK MASTER</h1>
    <h2>COMP206 - Assignment 2</h2>
  </header>
</template>

<script>
export default {
  name: 'AppHeader'
};
</script>

<style scoped>
header {
position: sticky;
top: 0;
background-color: #ff9f1c; 
padding: 20px;
text-align: center;
border-bottom: 3px solid #ffbf69; 
color: #ffffff;
text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

h1 {
font-size: 36px;
margin: 0;
font-weight: bold;
text-transform: uppercase;
}

h2 {
font-size: 18px;
margin: 5px 0 0 0;
font-weight: normal;
}
</style>
s