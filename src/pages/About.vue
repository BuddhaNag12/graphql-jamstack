<template>
    <Layout>
        <div>
            <h1>About page</h1>
        </div>
    </Layout>
</template>

<script>
export default {
     metaInfo() {
    return {
      title: "About",
      meta: [
        { name: 'About', content: "this is the about page" }
      ],
      // etc...
    }
  }
}
</script>