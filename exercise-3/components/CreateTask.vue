<template>
  <div class="form">
    <div class="input-group">
      <input v-model="nameText" type="text" class="form-control">
      <span class="input-group-btn">
        <button @click="sendForm()" class="btn btn-default" type="button">
          <span class="glyphicon glyphicon-plus"></span> Add new task
        </button>
      </span>
    </div>
  </div>
</template>


<script>
  export default {
    data() {
      return {
        nameText: '',
      };
    },
    methods: {
      sendForm() {
        if (this.nameText.length > 0) {
          const name = this.nameText;
          this.$emit('add-task', {
            name,
            done: false,
          });
          this.nameText = '';
        }
        this.isCreating = false;
      },
    },
  };
</script>
