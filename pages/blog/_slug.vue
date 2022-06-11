<template>
  <div class="m-10">
    <NuxtLink to="/blog" class="text-md text-blue-700"
      >&lt;= Back to the blog</NuxtLink
    >
    <h1 class="text-3xl">{{ page.title }}</h1>
    <hr class="bg-blue-800 rounded-full" />
    <br />
    <nuxt-content :document="page" />
  </div>
</template>
<script>
export default {
  head() {
    return {
      title: this.page.title,
    };
  },
  async asyncData({ $content, params, error }) {
    const slug = params.slug || "index";
    const page = await $content("blog", slug)
      .fetch()
      .catch((err) => {
        error({ statusCode: 404, message: "This page could not be found" });
      });
    return {
      page,
    };
  },
};
</script>