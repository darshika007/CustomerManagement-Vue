<template>
  <div class="customers container">
    <h1 class="page-header">Manage Customers</h1>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Email</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for = "customer in customers">
          <td>{{customer.first_name}}</td>
          <td>{{customer.last_name}}</td>
          <td>{{customer.email}}</td>
          <td></td>
        </tr>
  </div>
</template>

<script>
export default {
  name: 'customers',
  data(){
    return{
      customers: []
    }
  },
  methods: {
    fetchCust(){
      this.$http.get('http://slimapp/api/customers')
      .then(function(response){
        this.customers = JSON.parse(response.body);
        this.customers = JSON.parse(response.body);
      });
    }
  },
  created: function(){
    this.fetchCust();
  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
