<script>
import { ref } from 'vue'
import axios from 'axios';

export default {
  data() {
    return {
      loading: true,
      error: null,
      data: null
    };
  },
  setup() {
    const count = ref(0)

    return {
      count
    }
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      axios.get('/data')
        .then(response => {
          this.data = response.data;
          console.log(this.data);
          this.loading = false;
        })
        .catch(error => {
          console.error('Error fetching data:', error);
          this.error = error.message;
          this.loading = false;
        });
    }
  }
}
</script>

<template>
  <div v-if="loading" id="app">Loading...</div>
  <div v-else id="app">
    <ul>
      <li><a>Master Parts changeover matrix</a></li>
      <li><a>Add Part</a></li>
    </ul>
    <div class="grid-container">
      <div class="grid-item"></div>
      <div class="grid-item">Part A</div>
      <div class="grid-item">Part B</div>
      <div class="grid-item">Part C</div>
      <div class="grid-item">Edit Time</div>
      <div class="grid-item">Part A</div>
      <div class="grid-item"></div>
      <div class="grid-item"><input type="number" v-model="data[0][1]"></div>
      <div class="grid-item"><input type="number" v-model="data[0][2]"></div>
      <div class="grid-item">Time</div>
      <div class="grid-item">Part B</div>
      <div class="grid-item"><input type="number" v-model="data[1][0]"></div>
      <div class="grid-item"></div>
      <div class="grid-item"><input type="number" v-model="data[1][2]"></div>
      <div class="grid-item">Time</div>
      <div class="grid-item">Part C</div>
      <div class="grid-item"><input type="number" v-model="data[2][0]"></div>
      <div class="grid-item"><input type="number" v-model="data[2][1]"></div>
      <div class="grid-item"></div>
      <div class="grid-item">Time</div>
    </div>
  </div>
</template>

<style>

</style>
