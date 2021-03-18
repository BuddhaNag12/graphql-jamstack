<template>
  <Layout>
    <div>
      <b-container class="mt-2" fluid>
        <b-row>
          <b-col
            sm="12"
            md="6"
            lg="4"
            v-for="edge in $page.posts.edges"
            :key="edge.node.id"
          >
            <b-card
              :title="edge.node.title"
              img-src="https://picsum.photos/600/300/?image=25"
              img-alt="Image"
              img-top
              tag="article"
              style="width: 20rem"
              class="mb-2"
            >
              <b-card-text style="text-overflow: elipses">
                {{ edge.node.body }}
              </b-card-text>

              <b-button
                @click="$router.push(`/ViewPosts/${edge.node.id}`)"
                variant="primary"
                >View More</b-button
              >
            </b-card>
          </b-col>
        </b-row>
        <b-col md="6" offset-md="4">
          <b-pagination-nav
            :linkGen="linkGen"
            :number-of-pages="$page.posts.pageInfo.totalPages"
          ></b-pagination-nav
        ></b-col>
      </b-container>
    </div>
  </Layout>
</template>

<page-query>

query ($page: Int) {
  posts:allRandomPosts(perPage: 10, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        title
        body
      }
    }
  }
}

</page-query>

<script>

export default {
  metaInfo: {
    title: "Home",
  },
  components: {
    Pager,
  },
  methods: {
     linkGen(pageNum) {
        return pageNum === 1 ? '/' : `/${pageNum}`
      }
  },
};
</script>

<style>
.home-links a {
  margin-right: 1rem;
}

.pager {
  font-size: 20px;
  display: flex;
}
.pager a {
  margin: 2px;
}
</style>
