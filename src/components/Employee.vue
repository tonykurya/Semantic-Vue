<template>


    <div class="ui cards">
      <div class="card">
        <div class="content" v-show="!isEditing">
          <img class="left floated mini ui image" src="https://secure.gravatar.com/avatar/0e678440e8e843eec12ec8aaa0e430e6">
          <div class="header">
          {{ employee.name }}
          </div>
          <div class="meta">
          {{ employee.role }}
          </div>
          <div class="description">

             <div class="extra content">
                <div class="ui two buttons">
                  <div class="ui orange button" v-on:click="showForm">Edit</div>
                    <div class="or"></div>
                  <div class="ui red button" v-on:click="deleteEmployee(employee)">Delete</div>
                </div>
              </div>  
          </div>
        </div>

    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Name</label>
          <input type='text' v-model="employee.name" >
        </div>
        <div class='field'>
          <label>Role</label>
          <input type='text' v-model="employee.role" >
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui red button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>

        
        <div class='ui bottom attached green basic button' v-show="!isEditing && employee.linked" disabled>
                  Floor Manager
        </div>
        <div class='ui bottom attached green button' v-on:click="linkEmployee(employee)" v-show="!isEditing && !employee.linked">
            Link
        </div>


      </div>
    </div>

</template>

<script type="text/javascript">
  export default {
    props: ['employee'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      linkEmployee(employee) {
        this.$emit('link-employee', employee);
      },
      deleteEmployee(employee) {
        this.$emit('delete-employee', employee);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>

<style type="text/css">
  .label {
    font-family: 'Quicksand', sans-serif;
  }
</style>
