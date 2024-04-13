
<template>
    <div class="flex-page">
      <div class="right">
        <div class="right-header">
          <h1>WELCOME TO Jokes</h1>
          <h1>Central</h1>
        </div>
        <div>
          <h3>Embark on a journey of random giggles</h3>
        </div>
        <div class="flex-jokes">
          <form @submit.prevent="fetchJokesByCategory"> <input type="text" v-model="selectedCategory" placeholder="Search for jokes..." />
            <button type="submit">Search</button>
          </form>
        </div>
        <div class="search-key">
          <button @click="fetchJokesByCategory('any')">any</button>
          <button @click="fetchJokesByCategory('programming')">programming</button>
          <button @click="fetchJokesByCategory('misc')">misc</button>
          <button @click="fetchJokesByCategory('dark')">dark</button>
          <button @click="fetchJokesByCategory('pun')">pun</button>
          <button @click="fetchJokesByCategory('christmas')">Christmas</button>
          <button @click="fetchJokesByCategory('spooky')">Spooky</button>

        </div>
      </div>
  
      <div class="left">
        <div class="header">
          <h1>Jokes Searched</h1>
          <h3>Here are some jokes we found for you!</h3>
        </div>

        <div class="jokes">
          <p v-for="joke in filteredJokes" :key="joke.id">
            {{ joke.joke }}
          </p>
        </div>



      </div>
    </div>
  </template>

<script>
  import axios from 'axios';
  
  export default {
  data() {
    return {
      jokes: [],
      isLoading: false,
      error: null,
      selectedCategory: '',
    };
  },
  computed: {
    filteredJokes() {
      return this.jokes.filter(joke => joke.joke);
    }
  },
  methods: {
    async fetchJokesByCategory(category) {
      try {
        this.isLoading = true;
        this.jokes = []; // Clear previous jokes
        this.error = null;
        const url = `https://v2.jokeapi.dev/joke/${category}?amount=10`;
        const response = await axios.get(url);
        if (response.status !== 200) {
          throw new Error(`Failed to fetch jokes. Status code: ${response.status}`);
        }
        this.jokes = response.data.jokes;
      } catch (error) {
        this.error = error.message;
      } finally {
        this.isLoading = false;
      }
    },
    async fetchRandomJokes() {
      const categories = ['any', 'programming', 'misc', 'dark', 'pun'];
      const randomCategory = categories[Math.floor(Math.random() * categories.length)];
      await this.fetchJokesByCategory(randomCategory);
    }
  },
  mounted() {
    this.fetchRandomJokes();
  }
};
  </script>
  
  
<style>
.flex-page {
  display: flex;
  background-color: #f5f5f5; /* Light gray background */
  height: 100vh; /* Assuming you want the page to fill the viewport height */
}

/* Right Section Styling */
.right {
  width: 45%; /* Adjust width as needed */
  background: linear-gradient(to right, #434343, #000000); /* Dark gradient background */
  color: white; /* White text for better contrast */
  padding: 0px;
}

.right-header {
  text-align: center;
  margin-bottom: 20px; /* Add some space after the header */
}

h1 {
  font-size: 2.5em; /* Larger heading size */
  margin-bottom: 10px; /* More space after headings */
  font-family: 'Lobster', cursive; /* Decorative font for headings */
}

h3 {
  font-size: 1.3em;
  font-style: italic; /* Italic style for subtitle */
  margin-bottom: 15px; /* More space after subtitle */
}

/* Search Jokes Section Styling */
.flex-jokes {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px; /* Add space below search section */
}

.search-key {
  display: flex;
  justify-content: space-between; /* Distribute buttons evenly */
  padding: 10px 20px;
}

.search-key input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  flex-grow: 1; /* Allow input to grow and fill available space */
  margin-right: 10px;
}

.search-key button {
  padding: 10px 15px;
  background-color: #993333; /* Dark red background for search button */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

/* Left Section Styling */
.left {
  width: 55%; /* Adjust width as needed */
  background-color: white;
  border-radius: 16px;
  padding: 20px;
}

.header {
  text-align: center;
}

/* Jokes & Buttons Styling */
p {
  background-color: #fafafa; /* Light gr~ay background for jokes */
  border-radius: 5px;
  padding: 15px;
  margin: 10px 0; /* Adjust margin for spacing between jokes */
  box-shadow: 0 0 2px rgba(0, 0, 0, 0.1); /* Subtle shadow for jokes */
}

button {
  padding: 8px 16px; /* Adjust padding for a better size */
  background-color: green; /* Dark red background for category buttons */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin: 5px; /* Add some margin between buttons */
}

/* Define base button style */
button {
  padding: 8px 16px;
  background-color: green; /* Initial green color */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

/* Define hover style (optional, for desktop interactions) */
button:hover {
  background-color: green; /* Lighter green on hover */
}

/* Define active style (for button press effect) */
button:active {
  background-color: rgb(0, 255, 13); /* Red color when pressed */
}

</style>