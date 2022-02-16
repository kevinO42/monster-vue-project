<template>
  <div class="main">
    <div class="card">
      <div class="card-header"><h5>User</h5></div>
      <div class="card-body">
        <BaseTable :headers="headers" :entries="entries" :sortable="sortable" />
      </div>
    </div>
  </div>
</template>

<script>
import BaseTable from '../components/BaseTable.vue'

export default {
  name: 'User',
  components: {
    BaseTable
  },
  data() {
    return {
      headers: [
        { name: 'avatar', text: '' },
        { name: 'name', text: 'Name' },
        { name: 'email', text: 'Email' },
        { name: 'date_of_birth', text: 'Date of Birth' },
        { name: 'credit_card', text: 'Credit Card' },
        { name: 'title', text: 'Title' },
        { name: 'status', text: 'Status' }
      ],
      entries: [],
      sortable: [ 'name', 'email', 'status' ]
    }
  },
  mounted() {
    fetch('https://random-data-api.com/api/users/random_user?size=20')
      .then(res => res.json())
      .then(data => this.entries = data)
      .catch(err => console.log(err.message))
  }
}
</script>
