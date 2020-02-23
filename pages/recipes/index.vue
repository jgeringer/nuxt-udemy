<template>
    <section class="recipes">
        <Recipe 
            v-for="recipe in recipes"
            :key="recipe.id"
            :title="recipe.title"
            :thumbnail="recipe.thumbnail"
            :id="recipe.id"
            :previewText="recipe.previewText">
        </Recipe>
    </section>
</template>

<script>
import Recipe from '@/components/Recipes/Recipe'

export default {
    components: {
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
}
</script>

<style scoped>
.recipes {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 1rem;
}
</style>
