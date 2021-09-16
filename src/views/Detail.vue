<template>
  <div>
    <div class="col-md-12">
      <div class="py-2 mb-2 border-bottom">
        <h3 class="fst-italic fw-bold">
          {{ detail.title }}
        </h3>
      </div>
      <article>
        <p>
          {{ detail.publishedAt }} by <span>{{ detail.author }}</span>
        </p>
        <div class="row">
          <div class="col-md-6">
            <div>
              <p>{{ detail.description }}</p>
              <p>{{ detail.content }}</p>
            </div>
          </div>
          <div class="col-md-6">
            <div class="l-pic" style="height: 360px">
              <img :src="detail.urlToImage" :alt="detail.title" />
            </div>
          </div>
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
import moment from "moment";
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
    this.detail.publishedAt = moment(this.detail.publishedAt).format(
      "MMM DD YYYY"
    );
  },
};
</script>
