<template>
  <div class="m-10">
    <div class="w-full shadow-xl min-h-10 p-10">
      <div class="flex">
        <div class="col">
          <img
            :src="`https://cdn2.scratch.mit.edu/get_image/user/${res.id}_100x100.png`"
          />
        </div>
        <div class="col ml-10">
          <h1 class="text-xl">{{ res.username }}</h1>
          <div class="tag bg-blue-100 rounded">
            {{ res.status }}
          </div>
        </div>
      </div>
    </div>
    <div class="flex" v-if="forumRes && forumRes.counts">
      <div class="col w-4/10 shadow-xl min-h-10 p-10">
        <h1 class="text-3xl">POSTPERCENT</h1>
        <div class="flex">
          <div class="col p-10">
            <p class="text-xl">TOTAL POSTS</p>
            <p class="text-md">
              {{ forumRes.counts ? forumRes.counts.total.count : "0" }}
            </p>
          </div>
          <div class="col p-10">
            <p class="text-xl">RANK</p>
            <p class="text-md">
              {{ forumRes.counts ? forumRes.counts.total.rank : "none" }}
            </p>
          </div>
        </div>
        <a
          :href="`https://postpercent.rirurin.com/users/${res.username}`"
          class="text-xl"
          >View on postpercent</a
        >
      </div>
    </div>
    <div class="flex" v-if="res && !res.error">
      <div class="col w-4/10 shadow-xl min-h-10 p-10">
        <h1 class="text-3xl">ScratchStats</h1>
        <div class="flex">
          <div class="col p-10">
            <p class="text-xl">POPULARITY RANK</p>
            <p class="text-md">
              {{ res.statistics ? res.statistics.views : "Invalid" }}
            </p>
          </div>
          <div class="col p-10">
            <p class="text-xl">COUNTRY</p>
            <p class="text-md">
              {{ res.country }}
            </p>
          </div>
        </div>
        <a :href="`https://scratchstats.com/${res.username}`" class="text-xl"
          >View on ScratchStats</a
        >
      </div>
    </div>
  </div>
</template>
<script>
export default {
  head() {
    return {
      title: `${this.$route.params.user} ~ user-viewer`,
    };
  },
  data() {
    return {
      slug: this.$route.params.user,
      res: {},
      history: {},
      forumRes: {},
    };
  },
  async fetch() {
    let res = await fetch(
      `${process.env.api}/scratch/user/${this.slug}/activity`
    );
    let json = await res.json();
    this.history = json;

    let scratchDbRes = await fetch(
      `https://scratchdb.lefty.one/v3/user/info/${this.slug}`
    );
    let json2 = await scratchDbRes.json();

    this.res = json2;

    let forumRes = await fetch(
      `https://scratchdb.lefty.one/v3/forum/user/info/${this.slug}`
    );

    this.forumRes = await forumRes.json();
  },
  fetchOnServer: false,
};
</script>
<style scoped>
.tag {
  padding: 4px;
}
</style>