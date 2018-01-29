<template>
  <div class="container">
    <h1>My ToDo App</h1>
    <CreateTask class="create-task" @add-task="addTask" />
    <TasksList :tasks="tasks" /> <!--przekazanie danych -->
  </div>
</template>


<script>
import 'bootstrap/dist/css/bootstrap.css';
import TasksList from './components/TasksList'; //uzycie komponentu 
import CreateTask from './components/CreateTask';

export default {
  name: 'app',
  components: { //uzycie komponentu
    TasksList,
    CreateTask,
  },
  methods: {
    addTask(task) {
      this.tasks.push(task);
    },
  },
  data() {
    return {
      tasks: [{
        id: 1,
        name: 'Learn about Vue.js and build ToDo App',
        done: true,
      }, {
        id: 2,
        name: 'Learn about Progressive Web Apps',
        done: false,
      }, {
        id: 3,
        name: 'Learn Node.js',
        done: false,
      }, {
        id: 4,
        name: 'Do JavaScript Course',
        done: true,
      },{
        id: 5,
        name: 'Learn Angular and build first app',
        done: false,
      }],
    };
  },
};
</script>


<style scoped>
  * {
    font-family: 'Indie Flower', cursive;
    font-size: 18px;
    background-color: #bdcfed;
;
  }

  h1 {
    font-family: 'Courgette', cursive;
  }

  .container {
    width: 500px;
  }
  
  .create-task {
    margin-bottom: 10px;
  }
</style>
