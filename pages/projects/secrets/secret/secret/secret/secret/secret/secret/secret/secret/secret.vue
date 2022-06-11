<template>
<p>:)</p>
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
      height: 100
    };
  },
  mounted() {
    window.location.href = 'https://youtube.com/embed/kbQS-rLmJv4?autoplay'
  },
};
</script>
