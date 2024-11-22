<template>
  <div id="app">
    <!-- Header Component -->
    <AppHeader />

    <!-- Main Content (Todo List) -->
    <main>
      <TodoList />
    </main>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    TodoList
  }
};
</script>

<style>
/* Import 8-bit font */
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

body {
  font-family: 'Press Start 2P', sans-serif;
  background-color: #ffffff; 
  color: #2ec4b6; 
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* General Section Styling */
section {
  background-color: #cbf3f0; 
  border-radius: 10px; 
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); 
  padding: 20px;
  margin: 20px auto;
  max-width: 600px;
  text-align: center;
}

/* Header Styling */
h3 {
  color: #ff9f1c; 
  font-size: 24px;
  margin-bottom: 20px;
}

/* Input Styling */
input[type='text'] {
  border: 2px solid #2ec4b6; 
  border-radius: 8px;
  padding: 10px;
  font-size: 14px;
  width: 80%;
  margin-bottom: 10px;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
}

input[type='text']:focus {
  outline: none;
  border-color: #ffbf69; 
  box-shadow: 0 0 8px #ffbf69;
}

/* Button Styling */
button {
  background-color: #ffbf69; 
  color: #ffffff;
  border: none;
  border-radius: 8px;
  padding: 10px 20px;
  font-size: 14px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

button:hover {
  background-color: #ff9f1c; 
  transform: scale(1.05); /* Slight zoom */
}

/* Todo List Styling */
ul {
  list-style: none;
  padding: 0;
}

li {
  background-color: #ffffff;
  border: 2px solid #cbf3f0;
  border-radius: 8px;
  padding: 10px 20px;
  margin: 10px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

li .completed {
  text-decoration: line-through;
  color: #ff9f1c; 
}

li:hover {
  border-color: #2ec4b6; 
  transform: translateY(-2px);
  transition: all 0.2s ease-in-out;
}

@media (max-width: 768px) {
  section {
    width: 90%;
  }

  input[type='text'] {
    width: 100%;
  }
}
</style>
