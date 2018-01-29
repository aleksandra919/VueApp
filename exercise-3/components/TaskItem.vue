<template>
  <li class="list-group-item" :class="{taskDone: task.done, taskToDo: !task.done}"> <!-- zmienia klase w zalezonosci czy task.done jest true czy false -->
    <span class="title name" v-show="!edit">{{task.name}}</span>
    <input class="name" v-model="task.name" v-show="edit"></input>
    <button class="btn btn-default btn-xs" v-if="!edit" @click="enableEditMode()">
      <span class="glyphicon glyphicon-pencil"></span>
    </button>
    <button class="btn btn-basic btn-xs" @click="disableEditMode()" v-else>
      <span class="glyphicon glyphicon-saved"></span>
    </button>
    <button class="btn btn-primary btn-xs" @click="changeStatus()">
      <span class="glyphicon glyphicon-remove" v-show="task.done"></span>
      <span class="glyphicon glyphicon-ok" v-show="!task.done"></span>
    </button>
    <button class="btn btn-danger btn-xs" @click="removeTask()">
      <span class="glyphicon glyphicon-trash"></span>
    </button>
  </li>
</template>

<script>
  export default {
    props: {
      task: {  //dane przekazane do komponentu z taskslist.vue.
        type: Object,
        required: true,
      },
    },    
    data() {
      return {
        edit: false,
        delete: false,
      };
    },
    methods: {
      enableEditMode(){
       this.edit = true;
      },
      disableEditMode(){
        this.edit = false;
      },
      changeStatus(){
        if(this.task.done == false) {
          this.task.done = true;
        } else {
          this.task.done = false;
        }
      },
      removeTask(){
        this.$emit('to-Be-Removed', this.task);
      },
    }
  };
</script>

<style>
.taskDone {
  color: #37893a;
  background: #e0f4ec;
  
}
.taskDone .name {
  text-decoration: line-through;
}
.taskToDo {
  color : red;
}
</style>