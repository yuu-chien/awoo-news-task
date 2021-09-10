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
      <a href="#" class="c-newsCard__link text-primary text-opacity-50"
        >Continue reading</a
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
};
</script>
