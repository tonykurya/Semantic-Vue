<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic green button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>Add User
    </button>
    <div class='ui card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Name</label>
            <input v-model="nameText" type='text'>
          </div>
          <div class='field'>
            <label>Role</label>
            <input v-model="roleText" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui teal button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nameText: '',
      roleText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.nameText.length > 0 && this.roleText.length > 0) {
        const name = this.nameText;
        const role = this.roleText;
        this.$emit('create-employee', {
          name,
          role,
          linked: false,
        });
        this.nameText = '';
        this.roleText = '';
        this.isCreating = false;
      }
    },
  },
};
</script>
