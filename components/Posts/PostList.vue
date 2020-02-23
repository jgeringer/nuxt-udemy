<template>
    <section>
        <h1 class="intro mb-3">Latest Articles</h1>
        <section class="posts-list mb-3">
            <PostPreview 
            v-for="post in posts"
            :key="post.id"
            :id="post.id" 
            :is-admin="isAdmin"
            :thumbnail="post.thumbnail"
            :title="post.title"
            :previewText="post.previewText" />
        </section>      
    </section>
</template>

<script>
import PostPreview from '@/components/Posts/PostPreview'
export default {
    components: {
        PostPreview
    },
    props: {
        isAdmin: {
            type: Boolean,
            default: false 
        },
        posts: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
    .intro {
        margin-top: 2rem;
    }
    .posts-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 1rem;
    }
</style>
