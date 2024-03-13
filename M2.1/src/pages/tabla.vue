<template>
    <Navbar />
    <v-container>
        <v-data-table :headers="headers" :items="todos" class="elevation-1"></v-data-table>
    </v-container>
</template>
  
<script>
import axios from 'axios';

export default {
    data: () => ({
        todos: [], 
        headers: [ 
            { title: 'ID', key: 'id' },
            { title: 'Title', key: 'title' },
            { title: 'Completed', key: 'completed' },
        ],
    }),
    created() {
        this.fetchData();
    },
    methods: {
        async fetchData() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/todos');
                this.todos = response.data;
            } catch (error) {
                console.error('There was an error fetching the data:', error);
            }
        }

    },
};

</script>
  