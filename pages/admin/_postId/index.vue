<template>
    <div class="admin-post-page">
        <section class="update-form">
            <AdminPostForm :post="loadedPost" />
        </section>
    </div>
</template>

<script>
import AdminPostForm from '@/components/Admin/AdminPostForm.vue';

export default {
    layout: 'admin',
    components: {
        AdminPostForm
    },
    data() {
        return {
            loadedPost: {
                author: "Max",
                title: "My awesome post!",
                content: "Super Amazing!",
                thumbnailLink: "https://images.unsplash.com/photo-1531297484001-80022131f5a1?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1420&q=80"
            }
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