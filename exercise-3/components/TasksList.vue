<template>
  <div>
      <p>Completed tasks: {{completedTasks.length}}</p>
      <ul class="list-group">
        <TaskItem v-for="task in tasks" :task="task" :key="task.id" @to-Be-Removed="toBeRemoved" /> <!-- jesli chce z taskItem wyemitowwac cos do taskList to musze to tutaj zdefiniowac, robie takie cos jak @click-->
      </ul>
    </div>
</template>

<script>
  import TaskItem from './TaskItem';

  export default {
    components: {
      TaskItem,
    },
    props: { //dane przekazane do komponentu z app.vue.
      tasks: {
        type: Array,
        required: true,
      },
    },
    methods:{
      toBeRemoved(task){
        const taskIndex = this.tasks.indexOf(task);
        this.tasks.splice(taskIndex, 1); //remove task
      }
    },
    //computed properties are cached based on their dependencies. A computed property will only re-evaluate when some of its dependencies have changed
    computed: {
      completedTasks: function (){
        return this.tasks.filter(task => task.done === true);
        //wyzej skrocona wersja tego: return this.tasks.filter(function(task){return task.done === true})
      },
    },
  };
</script>
