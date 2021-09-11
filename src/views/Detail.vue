<template>
  <div>
    <div class="col-md-12">
      <div class="py-2 mb-2 border-bottom">
        <h3 class="fst-italic fw-bold">
          {{ detail.title }}
        </h3>
      </div>
      <article>
        <p class="">
          January 1, 2021 by <span>{{ detail.author }}</span>
        </p>
        <p>{{ detail.description }}</p>
        <p>{{ detail.content }}</p>
        <div class="l-pic">
          <img :src="detail.urlToImage" :alt="detail.title" />
        </div>
      </article>
    </div>
    <div class="col-md-12 my-3">
      <router-link to="/" class="btn btn-outline-info"
        >Back to list</router-link
      >
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      detail: {},
    };
  },
  beforeCreate() {
    this.detail = {
      title: "",
      author: "",
      content: "",
      description: "",
      urlToImage: "",
      publishedAt: "",
    };
  },
  created() {
    this.detail = this.$route.params.data;
  },
};
</script>
