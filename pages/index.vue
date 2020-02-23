<template>
  <section class="container">

    <div class="home-page">
      <PostList :posts="loadedPosts" />
      <Weather />
    </div>

    </div>
  </section>
</template>

<script>
import PostList from '@/components/Posts/PostList'
import Weather from '@/components/Weather'

export default {
  components: {
    PostList,
    Weather
  },
  computed: {
    loadedPosts() {
      return this.$store.getters.loadedPosts
    }
  }
  
}
</script>

<style scoped>
.featured-posts {
  display: flex;
  padding: 20px;
  box-sizing: border-box;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}
</style>
