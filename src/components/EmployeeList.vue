<template>
  <div>

      <div class="ui card" style="background-color: #00B5AD; text-color: #fff;">
        <div class="content">
          <div class="header">Floor Managers</div>
          <div class="meta">{{staff.filter(employee => {return employee.linked === true}).length}}</div>
          <div class="header">Floor Staff</div>
          <div class="meta">{{staff.filter(employee => {return employee.linked === false}).length}}</div>
        </div>
      </div>

    <employee v-on:delete-employee="deleteEmployee" v-on:link-employee="linkEmployee" v-for="employee in staff" :employee.sync="employee"></employee>
  </div>
</template>

<script type = "text/javascript" >
import sweetalert from 'sweetalert';
import Employee from './Employee';

export default {
  props: ['staff'],
  components: {
    Employee,
  },
  methods: {
    deleteEmployee(employee) {
      sweetalert({
        title: 'Are you sure?',
        text: 'This Employee will be permanently deleted!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Yes, delete it!',
        closeOnConfirm: false,
      },
      () => {
        const employeeIndex = this.staff.indexOf(employee);
        this.staff.splice(employeeIndex, 1);
        sweetalert('Deleted!', 'This employee has been deleted.', 'success');
      });
    },
    linkEmployee(employee) {
      const employeeIndex = this.staff.indexOf(employee);
      this.staff[employeeIndex].linked = true;
      sweetalert('Success!', 'You have linked a Floor Manager!', 'success');
    },
  },
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>

