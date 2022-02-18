<template>
  <div class="main">
    <div class="card">
      <div class="card-header">
        <div class="row">
          <div class="col"><h5>User</h5></div>
          <div class="col text-right">
            <router-link :to="{ name: 'Registration' }" class="btn btn-primary btn-sm float-end">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-plus-circle-fill" viewBox="0 0 16 16">
                <path d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zM8.5 4.5a.5.5 0 0 0-1 0v3h-3a.5.5 0 0 0 0 1h3v3a.5.5 0 0 0 1 0v-3h3a.5.5 0 0 0 0-1h-3v-3z"/>
              </svg>&nbsp;
              <span>Create User</span>
            </router-link>
          </div>
        </div>
      </div>
      <div class="card-body overflow-auto">
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
