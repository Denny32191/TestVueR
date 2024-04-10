<template>
   <div class="card">
      <div class="card-body">
        <h5 class="card-title  post-title">{{ post.title }}</h5>
        <span class="card-subtitle mb-2 text-body-secondary post-text">{{ post.body }}</span>
        <p class="card-text  post-user" >{{ post.userName }}</p>
      </div>
    </div>
</template>
<script>
export default {
  name: "PostCard",
  props: {
    post: {
      type: Object, 
      required: true 
    }
  }
};
</script>

<style lang="scss" scoped>

.post-title {
  font-size: 18px;
  color: #0275d8;
}
.post-user {
  font-size: 14px;
  opacity: 0.5;
}
</style>
