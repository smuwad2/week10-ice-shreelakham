<script setup>
    // Import BlogPost component
    import BlogPost2 from './subcomponents/BlogPost2.vue';
import blogPost from './subcomponents/BlogPost2.vue'
	import axios from 'axios'
</script>

<script>
    export default {
        data() {
            return {
                posts: [] // array of post objects
            }  
        },

        components:{
            BlogPost2
        },

        computed: {
            baseUrl() {
                if (window.location.hostname == 'localhost')
                    return 'http://localhost:3000'
                else {
                    const codespace_host = window.location.hostname.replace('5173', '3000')
                    return `https://${codespace_host}`;
                }
            }
        },
        created() { // created is a hook that executes as soon as Vue instance is created
            axios.get(`${this.baseUrl}/posts`)
            .then(response => {
                // this gets the data, which is an array
                this.posts = response.data
                console.log(response.data)
            })
            .catch(error => {
                this.posts = [{ entry: 'There was an error: ' + error.message }]
            })
        },
        methods: {
            deletePost(id) {
                // TODO: Complete the delete method
                axios.get(`${this.baseUrl}/deletePost`, {params:{id : id}})

                    .then(response => {
                        // this gets the response data message
                        console.log(response.data.message)
                        // filter thru post array, and only take in posts where the id not = id , then add it to my posts array
                        this.posts = this.posts.filter(post=>post.id!=id)
                    })
                    .catch(error => {
                        console.log(error)
                    })

            }
        }
    }
</script>

<template>
   <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
<BlogPost2 v-for="post in posts" :subject="post.subject" :mood="post.mood"
:entry="post.entry" :id="post.id">
<button class="btn btn-primary" @click="deletePost(post.id)">Delete</button>
</BlogPost2>
</template>

