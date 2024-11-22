<template>
    <section>
      <h3>Today's Tasks</h3>
      <form @submit.prevent="addTodo">
        <input
          v-model="newTodoText"
          type="text"
          placeholder="Add a new task..."
        />
        <button type="submit">Add</button>
      </form>
  
      <p>
        Completed Tasks: {{ completedTodos }}/{{ totalTodos }}
      </p>
  
      <ul>
  <li v-for="(todo, index) in todos" :key="index">
    <!-- Clickable Text for Editing -->
    <span
      v-if="!todo.isEditing"
      :class="{ completed: todo.completed }"
      @click="editTodo(index)"
    >
      {{ todo.text }}
    </span>
    <input
      v-else
      v-model="todo.text"
      @keyup.enter="saveEdit(index)"
      @blur="saveEdit(index)"
      type="text"
    />

    <!-- Icon Buttons -->
    <div class="button-group">
      <img
        src="@/assets/accept.png"
        alt="Complete"
        class="icon"
        @click="toggleComplete(index)"
      />
      <img
        src="@/assets/remove.png"
        alt="Delete"
        class="icon"
        @click="deleteTodo(index)"
      />
    </div>
  </li>
</ul>
    </section>
  </template>
  
  

  <script>
  import { ref, computed, watch } from 'vue';
  
  export default {
    name: 'TodoList',
    setup() {
      // Load todos from local storage or use default values
      const todos = ref(
        JSON.parse(localStorage.getItem('todos')) || [
          { text: 'Learn Vue.js', completed: false, isEditing: false },
          { text: 'Build a Todo App', completed: true, isEditing: false },
          { text: 'Celebrate success!', completed: false, isEditing: false },
        ]
      );
  
      const newTodoText = ref('');
  
      const addTodo = () => {
        if (newTodoText.value.trim() !== '') {
          todos.value.push({
            text: newTodoText.value.trim(),
            completed: false,
            isEditing: false,
          });
          newTodoText.value = '';
        }
      };
  
      const toggleComplete = (index) => {
        todos.value[index].completed = !todos.value[index].completed;
      };
  
      const editTodo = (index) => {
        todos.value[index].isEditing = true;
      };
  
      const saveEdit = (index) => {
        todos.value[index].isEditing = false;
      };
  
      const deleteTodo = (index) => {
        todos.value.splice(index, 1);
      };
  
      // Computed properties for todo summary
      const totalTodos = computed(() => todos.value.length);
      const completedTodos = computed(() =>
        todos.value.filter((todo) => todo.completed).length
      );
  
      const allTasksCompleted = computed(() =>
        todos.value.length > 0 && todos.value.every((todo) => todo.completed)
      );
  
      // Watch for all tasks being completed
      watch(allTasksCompleted, (completed) => {
        if (completed) {
          launchConfetti();
        }
      });
  
      // Launch confetti when all tasks are completed
      const launchConfetti = () => {
        import('canvas-confetti').then((confetti) => {
          confetti.default({
            particleCount: 150,
            spread: 80,
            origin: { y: 0.6 },
          });
        });
      };
  
      // Watch for changes in todos and update local storage
      watch(
        todos,
        (newTodos) => {
          localStorage.setItem('todos', JSON.stringify(newTodos));
        },
        { deep: true }
      );
  
      return {
        todos,
        newTodoText,
        addTodo,
        toggleComplete,
        editTodo,
        saveEdit,
        deleteTodo,
        totalTodos,
        completedTodos,
        allTasksCompleted,
      };
    },
  };
  </script>
  

  
  <style scoped>
/* Section Styling */
section {
  background-color: transparent; 
  border: 2px solid #2ec4b6; 
  border-radius: 10px; 
  padding: 20px;
  margin: 20px auto;
  max-width: 600px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); 
}

/* Header Text */
h3 {
  color: #2ec4b6; 
  font-size: 24px;
  margin-bottom: 20px;
}

/* List Items */
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

li:hover {
  border-color: #2ec4b6; 
  transform: translateY(-2px);
  transition: all 0.2s ease-in-out;
}

/* Buttons (Icon Group) */
.button-group {
  display: flex;
  gap: 10px;
}

.icon {
  width: 24px; 
  height: 24px;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.icon:hover {
  transform: scale(1.2); 
}

/* Completed Task Styling */
.completed {
  text-decoration: line-through;
  color: #ffbf69; 
}

/* Input Styling */
input[type="text"] {
  border: 2px solid #2ec4b6; 
  border-radius: 8px;
  padding: 10px;
  font-size: 14px;
  width: 80%;
  margin-bottom: 10px;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
}

input[type="text"]:focus {
  outline: none;
  border-color: #ffbf69; 
  box-shadow: 0 0 8px #ffbf69;
}

@media (max-width: 768px) {
  section {
    width: 90%;
  }

  input[type="text"] {
    width: 100%;
  }
}
</style>

  