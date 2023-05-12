<template>
    <div class="posts">
            <div>
                <div><strong>Название:</strong>{{ post.title }}</div>
                <div><strong>Описание:</strong>{{ post.body }}</div>
            </div>
            <div class="post__btns">
                <my-button @click="$emit('remove', post)">Удалить</my-button>
            </div>
        </div>
</template>

<script>

    export default {
        
        props: {
            post: {
                type: Object,
                required: true, 
            }
        }
    }
</script>

<style>
    .posts {
        padding: 15px;
        border: solid 2px teal;
        margin-top: 15px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

</style>