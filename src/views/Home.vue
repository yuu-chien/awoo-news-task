<template>
  <div class="row">
    <h2 class="col-md-12 fw-bold fs-3">Find New Stuff</h2>
    <div class="col-md-12 mb-5">
      <div class="w-100 mb-2">
        <!-- <label for="" class="form-label"></label> -->
        <input type="text" class="form-control" id="" placeholder="COVID-19" />
      </div>
      <button type="button" class="btn btn-outline-info">Search</button>
    </div>
    <div class="col-md-12 col-lg-6" v-for="(item, i) in allnews" :key="i">
      <NewsCard :news="item"></NewsCard>
    </div>
  </div>
</template>

<script>
import NewsCard from "@/components/NewsCard.vue";
export default {
  components: {
    NewsCard,
  },
  props: ["news"],
  data() {
    return {
      uuid: process.env.VUE_APP_UUID,
      allnews: [],
    };
  },
  methods: {
    getNews() {
      this.axios
        .get(`https://newsapi.org/v2/everything?q=bitcoin&apiKey=${this.uuid}`)
        .then((res) => {
          if (res.status === 200) {
            this.allnews = res.data.articles;
          }
        });
    },
  },
  created() {
    this.getNews();
  },
};
</script>
