<template>
  <div class="card-columns">
    <PostCard v-for="post in posts" :key="post.id" :post="post" />
  </div>
</template>

<script>
import PostCard from "./PostСard.vue";

export default {
  props: {
    posts: { type: Array, required: true, default: () => [] },
  },
  components: {
    PostCard,
  },
};
</script>

<style lang="scss" scoped>

.card {
    break-inside: avoid; 
    margin-bottom: 20px;
}
@media (min-width: 576px) {
  .card-columns {
    column-count: 1;
  }
}
@media (min-width: 768px) {
  .card-columns {
    column-count: 2;
  }
}
@media (min-width: 992px) {
  .card-columns {
    column-count: 3;
  }
}
</style>
