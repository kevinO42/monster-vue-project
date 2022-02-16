<template>
  <table class="table">
    <thead>
    <tr v-for="th in tableHeaders" :key="th">
        <th scope="col">{{ th.name }}</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="td in tableEntries" :key="td">
        <td>{{ td.avatar }}</td>
        <td>{{ td.first_name + ' ' + td.last_name }}</td>
        <td>{{ td.email }}</td>
        <td>{{ td.date_of_birth }}</td>
        <td>{{ td.title }}</td>
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