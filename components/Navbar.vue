<template>
  <div class="shadow-md bg-blue-800 flex">
    <div v-for="item in items" :key="item">
      <div
        class="ease duration-500 inline-block text-gray-100 py-2 px-5 hover:text-gray-200 hover:text-underline hover:bg-blue-500"
      >
        <NuxtLink :to="item.link">
          {{ item.name }}
        </NuxtLink>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      items: [
        {
          name: "Home",
          link: "/",
        },
        {
          name: "Blog",
          link: "/blog",
        },
        {
          name: "Projects",
          link: "/projects",
        },
      ],
    };
  },
};
</script>