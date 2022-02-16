<template>
  <table class="table">
    <thead>
    <tr>
        <th v-for="th in tableHeaders" :key="th" scope="col">
            <span @click="sort(th.name)">
                <span v-if="sortable.includes(th.name)"> 
                    <svg v-if="!sortParams.name && !sortParams.direction" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-expand" viewBox="0 0 16 16">
                        <path fill-rule="evenodd" d="M3.646 9.146a.5.5 0 0 1 .708 0L8 12.793l3.646-3.647a.5.5 0 0 1 .708.708l-4 4a.5.5 0 0 1-.708 0l-4-4a.5.5 0 0 1 0-.708zm0-2.292a.5.5 0 0 0 .708 0L8 3.207l3.646 3.647a.5.5 0 0 0 .708-.708l-4-4a.5.5 0 0 0-.708 0l-4 4a.5.5 0 0 0 0 .708z"/>
                    </svg>

                    <svg v-if="sortParams.name === th.name && sortParams.direction === 'asc'" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-up" viewBox="0 0 16 16">
                        <path fill-rule="evenodd" d="M8 15a.5.5 0 0 0 .5-.5V2.707l3.146 3.147a.5.5 0 0 0 .708-.708l-4-4a.5.5 0 0 0-.708 0l-4 4a.5.5 0 1 0 .708.708L7.5 2.707V14.5a.5.5 0 0 0 .5.5z"/>
                    </svg>
                    
                    <svg v-if="sortParams.name === th.name && sortParams.direction === 'desc'" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-down" viewBox="0 0 16 16">
                        <path fill-rule="evenodd" d="M8 1a.5.5 0 0 1 .5.5v11.793l3.146-3.147a.5.5 0 0 1 .708.708l-4 4a.5.5 0 0 1-.708 0l-4-4a.5.5 0 0 1 .708-.708L7.5 13.293V1.5A.5.5 0 0 1 8 1z"/>
                    </svg>
                </span>
                {{ th.text }}
            </span>
        </th>
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
        <td>{{ td.subscription.status }}</td>
    </tr>
    </tbody>
  </table>
</template>

<script>
export default {
    name: 'BaseTable',
    props: {
        headers: Array,
        entries: Array,
        sortable: Array,
    },
    data() {
        return {
            sortParams: {
                name: '',
                direction: ''
            }
        }
    },
    methods: {
        sort(name) {
            this.sortParams.name = name
            this.sortParams.direction =  this.sortParams.direction === 'asc' ? 'desc' : 'asc';
        }
    },
    computed: {
        tableHeaders() {
            return this.headers || []
        },

        tableEntries() {
            if (!this.entries) {
                return []
            }

            if (!this.sortParams.direction)	{
                return this.entries
            }

            if (this.sortParams.direction === 'asc') {
                return this.entries.sort((a,b) => {
                    if (this.sortParams.name === 'name') {
                        let fa = a.first_name.toLowerCase(), fb = b.first_name.toLowerCase();
                        
                        if (fa < fb) {
                            return -1
                        }
                        if (fa > fb) {
                            return 1
                        }
                        return 0
                    }

                    if (this.sortParams.name === 'email') {
                        let fa = a.email.toLowerCase(), fb = b.email.toLowerCase();
                        
                        if (fa < fb) {
                            return -1
                        }
                        if (fa > fb) {
                            return 1
                        }
                        return 0
                    }

                    if (this.sortParams.name === 'status') {
                        let fa = a.subscription.status.toLowerCase(), fb = b.subscription.status.toLowerCase();
                        
                        if (fa < fb) {
                            return -1
                        }
                        if (fa > fb) {
                            return 1
                        }
                        return 0
                    }
                })
            }

            if (this.sortParams.direction === 'desc') {
                return this.entries.sort((a,b) => {
                    if (this.sortParams.name === 'name') {
                        let fa = a.first_name.toLowerCase(), fb = b.first_name.toLowerCase();
                        
                        if (fa > fb) {
                            return -1
                        }
                        if (fa < fb) {
                            return 1
                        }
                        return 0
                    }

                     if (this.sortParams.name === 'email') {
                        let fa = a.email.toLowerCase(), fb = b.email.toLowerCase();
                        
                        if (fa > fb) {
                            return -1
                        }
                        if (fa < fb) {
                            return 1
                        }
                        return 0
                    }

                     if (this.sortParams.name === 'status') {
                        let fa = a.subscription.status.toLowerCase(), fb = b.subscription.status.toLowerCase();
                        
                        if (fa > fb) {
                            return -1
                        }
                        if (fa < fb) {
                            return 1
                        }
                        return 0
                    }
                })
            }
        }
    }
}
</script>