<template>
  <Layout>
    <h1>{{ $page.Post.title }}</h1>
    <p>{{ $page.Post.body }}</p>
  </Layout>
</template>

<page-query>
query ($id: ID!) {
  Post:randomPosts(id: $id) {
    id
    title,
    body
  }
}
</page-query>

<script>
export default {
   metaInfo() {
    return {
      title: this.$page.Post.title,
      meta: [
        { name: 'Post', content: this.$page.Post.title }
      ],
      // etc...
    }
  }
};
</script>