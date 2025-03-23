<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

#search-app {
  max-width: 1024px;
  width: 100%;
}
.card {
  min-width: 33%;
}
.card .hl-search {
  background-color: yellow;
}
@media only screen and (max-width: 786px) {
  .card {
    min-width: 50%;
  }
}
@media only screen and (max-width: 480px) {
  .card {
    min-width: 100%;
  }
}
</style>

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <input type="text" v-model="searchTerm" placeholder="Search for posts..." />

    <div v-for="post in apiData" :key="post.id" class="card">
      <h3 v-html="highlight(post.title)"></h3>
      <p v-html="highlight(post.body)"></p>
    </div>
  </div>
</template>

<script>
// Import Vue's Composition API functions
import { ref } from 'vue';

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  setup() {
    // Reactive references using Vue's Composition API
    const searchTerm = ref('');
    const apiData = ref([
      {
        id: 1,
        title: 'Rich Text Improvements',
        body: 'The heart of content creation in Apostrophe has always been our rich text editor...',
      },
      {
        id: 2,
        title: 'Rich Text Improvements',
        body: 'The heart of content creation in Apostrophe has always been our rich text editor...',
      },
      {
        id: 3,
        title: 'Rich Text Improvements',
        body: 'The heart of content creation in Apostrophe has always been our rich text editor...',
      },
      {
        id: 4,
        title: 'Rich Text Improvements',
        body: 'The heart of content creation in Apostrophe has always been our rich text editor...',
      },
    ]);

    // Method to highlight the search term in the post content
    const highlight = (data) => {
      if (searchTerm.value) {
        const pattern = new RegExp(searchTerm.value, 'gi'); // Case-insensitive and global search

        return data.replace(pattern, (match) => {
          return `<span style="background-color: yellow;">${match}</span>`; // Wrap matching text in <span>
        });
      }
      return data; // Return the text as is if no search term
    };

    // Returning the reactive state and methods to the template
    return {
      searchTerm,
      apiData,
      highlight,
    };
  },
};
</script>

<style scoped>

ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

#search-app {
  max-width: 1024px;
  width: 100%;
}
.card {
  min-width: 33%;
}
 .hl-search {
  background-color: yellow;
}
@media only screen and (max-width: 786px) {
  .card {
    min-width: 50%;
  }
}
@media only screen and (max-width: 480px) {
  .card {
    min-width: 100%;
  }
}
</style>
