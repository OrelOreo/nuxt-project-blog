<template>
    <div class="admin-page">
        <section class="new-post">
            <AppButon @click="$router.push('/admin/new-post')">Create Post</AppButon>
        </section>
        <section class="existing-posts">
            <h1>Existing Posts</h1>
            <PostList isAdmin
            :posts="loadedPosts" />
        </section>
    </div>
</template>

<script>
import AppButon from "@/components/UI/AppButton"
import PostList from "@/components/Posts/PostList"

export default {
  layout: 'admin',
    components: {
        PostList,
        AppButon
    },
    computed: {
      loadedPosts() {
        return this.$store.getters.loadedPosts
      }
    }
}
</script>

<style scoped>
.admin-page {
  padding: 20px;
}

.new-post {
  text-align: center;
  border-bottom: 2px solid #ccc;
  padding-bottom: 10px;
}

.existing-posts h1 {
  text-align: center;
}
</style>