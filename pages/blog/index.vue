<template>
  <div class="flex">
    <div
      class="blog-post-card p-8 m-8 w-96 border-2 border-blue-700 shadow-lg cursor-pointer"
      :key="Math.random()"
      v-for="post in posts"
    >
      <NuxtLink :to="{ name: 'blog-slug', params: { slug: post.slug } }">
        <p class="text-3xl">{{ post.title }}</p>
        <p class="text-base">{{ post.description }}</p>
      </NuxtLink>
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params }) {
    let res = await $content("blog")
      .only(["title", "description", "date", "slug"])
      .sortBy("date", "desc")
      .fetch();

    return {
      posts: res,
    };
  },
};
</script>
