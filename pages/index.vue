<template>
  <section class="container">

    <div class="home-page">

      <section>
        <h1 class="intro mb-4 mt-5">Latest Recipes</h1>
        <div class="RecipeList">
          <Recipe 
              v-for="recipe in recipes"
              :key="recipe.id"
              :title="recipe.title"
              :thumbnail="recipe.thumbnail"
              :id="recipe.id"
              :previewText="recipe.previewText">
          </Recipe>
        </div>
      </section>

      <Weather />

      <PostList :posts="loadedPosts" />

    </div>

    </div>
  </section>
</template>

<script>
import PostList from '@/components/Posts/PostList'
import Weather from '@/components/Weather'
import Recipe from '@/components/Recipes/Recipe'

export default {
  components: {
    PostList,
    Weather,
    Recipe
  },
  asyncData() {   // <- get's new data for this vue
      return new Promise((resolve, reject) => {
          setTimeout(() => {
              resolve({
                  recipes: [
                      {
                          id: '1',
                          title: 'Burger',
                          thumbnail: 'https://amp.businessinsider.com/images/5a7dc169d03072af008b4bf2-750-562.jpg',
                          previewText: 'Awesome Burger!'
                      },
                      {
                          id: '2',
                          title: 'Ramen',
                          thumbnail: 'https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/190208-delish-ramen-horizontal-093-1550096715.jpg?crop=1xw:0.9995002498750624xh;center,top&resize=480:*',
                          previewText: 'A very good ramen recipe'
                      }
                  ]
              })
          }, 0); // 1500);
      })
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
.RecipeList {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 1rem;
}
</style>
