<template>
    <div class="app">
        <h1>Страница с задачами</h1>
        <div class="app__btns">
            <my-button
                @click="showDialog"
                style="margin: 15px 0;">Создать
            </my-button>
            <my-select/>
        </div>
        
        <my-dialog 
            v-model:show="dialogVisible">
            <post-form
            @create="createPost"/>
        </my-dialog>
        <post-list
            :posts="posts"
            @remove="removePost"
            v-if="!isPostLoading"/>
        <div v-else>Идет загрузка...</div>
    </div>
</template>

<script>
    import PostForm from './components/PostForm.vue';
    import PostList from './components/PostList.vue';
    import axios from 'axios';

    export default {
        components: {
            PostForm, PostList,
        },
        data () {
            return {
                posts: [],
                dialogVisible: false,
                isPostLoading: false,
            }
        },

        methods: {
            createPost (post) {
                this.posts.push(post);
                this.dialogVisible =false;
            },

            removePost (post) {
                this.posts = this.posts.filter(p => p.id !== post.id)
            },
            showDialog() {
                this.dialogVisible = true;
            },

            async fetchPosts () {
                try{
                    this.isPostLoading = true;
                    setTimeout( async() => {
                        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
                        this.posts = response.data;
                        this.isPostLoading = false;
                    }, 1000)
                    
                } catch(e) {
                    alert('Ошибка запроса!')
                }
            },

        },
        mounted() {
            this.fetchPosts();
        },
    }
</script>

<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .app {
        padding: 20px;
    }

    .app__btns {
        display: flex;
        justify-content: space-between;
    }
</style>