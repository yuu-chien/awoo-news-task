<template>
  <div class="col-12">
    <div class="l-pic" style="height: 360px">
      <img
        src="https://images.unsplash.com/photo-1585007600263-71228e40c8d1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=750&q=80"
        alt=""
      />
    </div>
    <div class="row">
      <div class="col-md-12 my-4">
        <div class="row">
          <div class="col-md-5">
            <input
              type="text"
              class="form-control"
              id=""
              placeholder="Keyword"
              v-model="keyword"
            />
          </div>
          <div class="col-md-5">
            <select class="form-select" v-model="optionval">
              <option disabled value="">Sort By...</option>
              <option value="Popularity">Popularity</option>
              <option value="Relevancy">Relevancy</option>
            </select>
          </div>
          <div class="col-md-2">
            <button
              type="button"
              class="btn btn-outline-info"
              @click.prevent="getNews()"
            >
              Search
            </button>
          </div>
        </div>
      </div>
      <div class="col-md-12 col-lg-6" v-for="(item, i) in allnews" :key="i">
        <NewsCard :news="item"></NewsCard>
      </div>
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
      optionval: "",
      keyword: "Taiwan",
    };
  },
  methods: {
    getNews() {
      this.axios
        .get(
          `https://newsapi.org/v2/everything?q=${this.keyword}&sortBy=${this.optionval}&apiKey=${this.uuid}`
        )
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
