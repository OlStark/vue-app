<template>
     <div v-if="posts.length > 0">
        <h3>Список задач:</h3>
        <post-item 
            v-for="post in posts"
            :post="post"
            :key="post.id"
            @remove="$emit('remove', post)"></post-item>
     </div>
     <h3 v-else style="color: red;"> Нет текущих задач!</h3>
</template>

<script>
    import PostItem from '../components/PostItem.vue'; 
    export default {
        components: {PostItem},
        props: {
            posts: {
                type: Array,
                required: true,
            }
        }
    }
</script>

<style scoped>


</style>