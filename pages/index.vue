<template>
  <div class="main m-0">
    <div class="m-0 shadow-2xl grid">
      <br />
      <br />
      <h1 class="text-4xl ml-28">Hey, I'm</h1>
      <h2 class="font-bold text-5xl ml-28 cursor-pointer">
        <a @click="change()">{{ type }}</a>
      </h2>
      <p class="text-2xl text-gray-500 ml-28">A beginner web dev</p>
      <br />
      <br />
      <br />
      <br />
      <br />
      <br />
    </div>
    <br />
    <br />
    <br />
    <div class="content p-10">
      <h1
        class="text-3xl align-right text-blue-800 font-semibold leading-8 sm:text-4xl mt-2"
      >
        Welcome to my site!
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      type: "rellyepikprograma",
    };
  },
};
</script>
