<template>
  <div id="app">
    <div class="container">
      <div class="search-input-wrapper">
        <InputSearch  v-model="searchQuery" @get-posts-to-view="getFilter" />
      </div>
      <PostsCard :posts="filteredPosts" />
    </div>
  </div>
</template>

<script>
import InputSearch from "./components/InputSearch.vue";
import PostsCard from "./components/PostsCard.vue";

export default {
  name: "App",
  components: {
    InputSearch,
    PostsCard,
  },
  data() {
    return {
      posts: [],
      filteredPosts: [],
      searchQuery: "",

      
    };
  },
  created() {
  this.loadData().then(() => this.getFilter())
},
  methods: {
    async loadData() {
      try {
        const postsResponse = await fetch("https://jsonplaceholder.typicode.com/posts");
        const usersResponse = await fetch("https://jsonplaceholder.typicode.com/users");

        const posts = await postsResponse.json();
        const users = await usersResponse.json();

        this.posts = posts.map((post) => {
          const user = users.find(({ id }) => id === post.userId);
          return { ...post, userName: user ? user.name : "Unknown" };
        });

        
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    },
    getFilter(value = '') {
      this.filteredPosts = this.posts.filter((post) => 
        post.userName.toLowerCase().includes(value.trim().toLowerCase())
      );
    },
  },
};
</script>

<style lang="scss">
html,
body {
  height: 100%;
  width: 100%;
}
body {
  margin: 0;
}
#app {
  width: 100%;
  min-height: 100%;
  font-size: 16px;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #2c3e50;
  background-color: #f8f9fa;
}
.container {
  width: 1200px;
  height: 100%;
  margin: 0 auto;
}
.search-input-wrapper {
  padding-top: 20px;
  margin-bottom: 20px;
}
@media (max-width: 576px) {
  .container {
    width: 350px;
  }
}
</style>
