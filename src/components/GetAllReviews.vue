<!-- YourVueComponent.vue -->
<template>
    <div>
        <button @click="getAllReviews">Get Latest Reviews</button>
        <div v-if="titles.length > 0">
            <!-- Display titles here -->
            <ul class="m-0 p-0">
                <p v-for="(title, index) in titles" :key="index">{{ title }}</p>
            </ul>
        </div>
        <div v-else>
            No titles available.
        </div>
    </div>
</template>
  
<script>
// Import axios
import axios from 'axios';

export default {
    data() {
        return {
            titles: [],
        };
    },
    methods: {
        async getAllReviews() {
            try {
                // Using axios
                const response = await axios.get('https://localhost:7011/BlogPost');
                this.titles = response.data.map(item => item.title);
            } catch (error) {
                console.error('Error fetching data:', error);
            }
        },
    },
    mounted() {
        // Call fetchData method when the component is mounted (page load)
        this.getAllReviews();
    },
};
</script>
  
<style>
/* Your component styles here */
</style>
  