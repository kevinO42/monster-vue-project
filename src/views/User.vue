<template>
  <div class="main">
    <div class="card">
      <div class="card-header"><h5>Dashboard</h5></div>
      <div class="card-body">
        <BaseTable :headers="headers" :entries="entries" />
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
        { name: 'title', text: 'Title' }
      ],
      entries: []
    }
  },
  mounted() {
    fetch('https://random-data-api.com/api/users/random_user?size=20')
      .then(res => res.json())
      .then(data => this.entries = data)
      .catch(err => err.message)
  }
}
</script>

<style>

</style>
