<template>
<div class= page>
      <div class="row">
        <div class="btn-group col-md-2 offset-md-5">
          <button
            type="button"
            class="btn btn-sm btn-outline-secondary"
            v-if="page != 1"
            @click="page--"
          >Previous</button>
          <button
            type="button"
            class="btn btn-sm btn-outline-secondary"
            v-for="pageNumber in pages.slice(page-1, page+5)"
            :key="pageNumber"
            @click="page = pageNumber"
          >{{pageNumber}}</button>
          <button
            type="button"
            class="btn btn-sm btn-outline-secondary"
            v-if="page < pages.length"
            @click="page++"
          >Next</button>
        </div>
      </div>
 </div>
</template>

<script>
export default {
  data() {
    return {
      books: [],
      // baseURL: `http://localhost:3000`,
      page: 1,
      perPage: 10,
      pages: []
    };
  },
  // created() {
  //   this.getArticles();
  // },
  methods: {
    // getArticles: async function() {
    //   const res = await this.axios.get(`${this.baseURL}/articles`);
    //   this.articles = res.data.articles;
    // },
    pagination: function() {
      const numberOfPages = Math.ceil(this.articles.length / this.perPage);
      for (let i = 1; i <= numberOfPages; i++) this.pages.push(i);
    },
    paginate: function(pageNumber) {
      const page = this.page;
      const perPage = this.perPage;
      const from = page * perPage - perPage;
      const to = page * perPage;
      return pageNumber.slice(from, to);
    }
  },
  // computed: {
  //   displayPage: function() {
  //     return this.paginate(this.pageNumber);
  //   }
  // },
  // watch: {
  //   articles() {
  //     this.setArticles();
  //   }
  // }
};
</script>


<style lang="css">
.pagination {
}
.page-item {
}
</style> 