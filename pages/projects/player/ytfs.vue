<template>
  <div class="m-10">
    <p>Redirecting</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      video: this.$route.query.v,
    };
  },
  mounted() {
    window.location.href = `../fullscreen-youtube-player/play?v=${this.video}`;
  },
};
</script>