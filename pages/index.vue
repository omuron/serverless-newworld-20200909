<template>
  <div class="container">
    <ul>
      <li v-for="(post, index) in posts.posts" :key="index">
        <a v-bind:href="'/post/' + post.ID">{{ post.title }}</a>
        <br />
        <span style="font-size: 0.6em; font-color: grey">{{ post.date }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const url =
      "https://public-api.wordpress.com/rest/v1.1/sites/keisuke69.wordpress.com/posts/";
    const response = await $axios.$get(url);
    return {
      posts: response,
    };
  },
};
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  /* text-align: center; */
}

li {
  list-style-type: none;
  font-size: 1.3em;
}
</style>
