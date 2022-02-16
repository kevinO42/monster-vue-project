<template>
  <table class="table">
    <thead>
    <tr>
        <th v-for="th in tableHeaders" :key="th" scope="col">{{ th.text }}</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="td in tableEntries" :key="td">
        <td><img :src="td.avatar" class="img-thumbnail rounded-circle" width="30" height="30"></td>
        <td>{{ td.first_name + ' ' + td.last_name }}</td>
        <td>{{ td.email }}</td>
        <td>{{ td.date_of_birth }}</td>
        <td>{{ td.credit_card.cc_number }}</td>
        <td>{{ td.employment.title }}</td>
    </tr>
    </tbody>
  </table>
</template>

<script>
export default {
    name: 'BaseTable',
    props: {
        headers: Array,
        entries: Array
    },
    computed: {
        tableHeaders() {
            return this.headers || []
        },

        tableEntries() {
            return this.entries || []
        }
    }
}
</script>