<template>
  <div class="c-newsCard border rounded shadow-sm mb-4">
    <div class="c-newsCard__cnt col-7 p-3">
      <div class="">
        <div class="c-newsCard__tit text-info mb-2">{{ news.title }}</div>
        <div class="c-newsCard__subtit text-muted">
          {{ news.publishedAt }} by {{ news.author }}
        </div>
      </div>
      <p class="c-newsCard__dec">{{ news.description }}</p>
      <a
        href="#"
        class="c-newsCard__link text-primary text-opacity-50"
        @click.prevent="readMore(news)"
        >Read more</a
      >
    </div>
    <div class="c-newsCard__img col-5">
      <img :src="news.urlToImage" :alt="news.title" />
    </div>
  </div>
</template>

<script>
export default {
  props: ["news"],
  data() {
    return {
      tempDetail: {},
    };
  },
  methods: {
    readMore(e) {
      this.tempDetail = e;
      // console.log(this.tempDetail);
      this.$router.push({
        name: "Detail",
        params: { data: this.tempDetail },
      });
    },
  },
};
</script>
