<template>
    <div class="admin-post-page">
        <section class="update-form">
            <AdminPostForm :post="loadedPost" @submit="onSubmitted" />
        </section>
    </div>
</template>

<script>
import AdminPostForm from '@/components/Admin/AdminPostForm.vue';
import axios from "axios"

export default {
    layout: 'admin',
    components: {
        AdminPostForm
    },
    asyncData(context) {
        return axios.get(`https://nuxt-blog-a5d79-default-rtdb.europe-west1.firebasedatabase.app/posts/${context.params.postId}.json`)
        .then(res => {
            return {
                loadedPost: res.data
            }
        })
        .catch(e => context.error())
    },
    methods: {
        onSubmitted(editedPost) {
            axios.put(`https://nuxt-blog-a5d79-default-rtdb.europe-west1.firebasedatabase.app/posts/${this.$route.params.postId}.json`, editedPost)
            .then(res => {
                this.$router.push('/admin')
            })
            .catch(e => console.log(e))
        }
    }
}
</script>

<style scoped>
.new-post-form {
    width: 90%;
    margin: 20px auto;
}
@media (min-width: 768px) {
    .new-post-form {
        width: 500px;
    }
}
</style>