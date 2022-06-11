<template>
  <iframe
    :src="`https://youtube.com/embed/${id}?autoplay=true`"
    :width="width"
    :height="height"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
  ></iframe>
</template>
<script>
export default {
  layout: "blank",
  head() {
    return {
      title: "Fullscreen YouTube Player",
    };
  },
  data() {
    return {
      width: 100,
      height: 100,
      id: this.$route.query.v || "dQw4w9WgXcQ",
    };
  },
  mounted() {
    let _this = this;
    function resize() {
      _this.width = window.innerWidth;
      _this.height = window.innerHeight;
    }

    window.addEventListener("resize", resize);
    resize();
  },
};
</script>
<style>
body {
  overflow: hidden;
}
</style>