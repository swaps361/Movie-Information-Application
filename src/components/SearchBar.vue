<template>
  <div class="search-container">
    <input type="text" v-model="query" placeholder="Search for a movie...">
    <button @click="search">Search</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: ''
    };
  },
  methods: {
    search() {
      this.$emit('search', this.query.trim());
    }
  }
};
</script>

<style scoped>

.search-container {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.search-container input[type="text"] {
  padding: 10px;
  width: 70%;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.search-container button {
  padding: 10px 20px;
  background-color: #000; 
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.search-container button:hover {
  background-color: #333; 
}
</style>
