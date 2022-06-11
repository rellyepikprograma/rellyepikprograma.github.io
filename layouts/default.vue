<template>
  <div>
    <div class="nav">
      <Navbar />
    </div>
    <div class="main">
      <Nuxt />
    </div>
    <div class="footer">
      <Footer />
    </div>
  </div>
</template>
<script>
export default {
  layout: "blank",
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Open+Sans&display=swap");
body {
  margin: 0;
}

.jumbotron-text-center * {
  float: center;
}

#content {
  margin-left: 10%;
}
</style>
