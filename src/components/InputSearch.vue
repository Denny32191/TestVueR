<template>
  <div class="input-group mb-3">
    <div class="input-group-text" id="basic-addon1">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="16"
        height="16"
        fill="currentColor"
        class="bi bi-search"
        viewBox="0 0 16 16"
      >
        <path
          d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"
        />
      </svg>
    </div>
    <input
      type="text"
      class="form-control"
      placeholder="Filter by author..."
      aria-label="Username"
      aria-describedby="basic-addon1"
      @input="searchUser($event)"
    />
  </div>
</template>

<script>
export default {
  name: "InputSearch",
  data() {
    return {
      placeholder: "Filter by author...",
    };
  },
  methods: {
    searchUser(event) {
      this.$emit("get-posts-to-view", event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>


.input-group {
  width: 354px;
  margin: 0 auto;
}

@media (max-width: 576px) {
  .input-group {
    width: 250px;
  }
}
</style>
