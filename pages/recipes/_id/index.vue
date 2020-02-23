<template>
    <section class="single-recipe">
        <h1>{{ recipe.title }}</h1>
        <div>
            <img :src="recipe.thumbnail" :alt="recipe.title" class="recipeImage">
        </div>
        <p>{{ recipe.previewText }}</p>
        <p class="mt-3">{{ recipe.content }}</p>
    </section>
</template>

<script>
export default {
    asyncData(context) {
        return new Promise((resolve, reject) => {
            setTimeout(() => {  //poc showing ajax request
                resolve({
                    recipe: [
                        {
                            id: '1',
                            title: 'Burger',
                            thumbnail: 'https://amp.businessinsider.com/images/5a7dc169d03072af008b4bf2-750-562.jpg',
                            previewText: 'Awesome Burger!',
                            content: 'When we went on the quest to make the world\'s best burger, we really wish we would have tested out an air fryer version. With the quick cook time, these burgers stay perfectly juicy and basically beg for a melty slice of cheese. Load it up with your favorite toppings and feel like the burger master you are - without all the smoke in your face.'
                        },
                        {
                            id: '2',
                            title: 'Ramen',
                            thumbnail: 'https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/190208-delish-ramen-horizontal-093-1550096715.jpg?crop=1xw:0.9995002498750624xh;center,top&resize=480:*',
                            previewText: 'A very good ramen recipe',
                            content: 'Making ramen from scratch is pretty darn elaborate. It can be a multiday affair, and if you simply don’t have time for it, it can seem very intimidating. (No, we’re not making our own noodles this time around...I’m taking it easy on you for now.) Our shoyu ramen recipe calls for making four important components: dashi and tare for the soup base, and nitamago and chashu as showstopping toppings. You can certainly eat a decent bowl of noodles without one or two of these players, but man oh man, magic happens when they all come together in one bite. Fear not: Your patience will be rewarded.'
                        }
                    ].find(el => el.id === context.params.id)
                })
            }, 0); //1500);
        })
    },
}
</script>

<style scoped>
    .single-recipe {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 1rem;
        flex-flow: column;
    }
    .recipeImage {
        height: 60vh;
    }
</style>
