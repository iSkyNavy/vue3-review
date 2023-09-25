<script setup>
import { ref } from 'vue';
import BlogPost from './components/BlogPost.vue';
import LoadingSpinnerVue from './components/LoadingSpinner.vue';
import PaginatePostVue from './components/PaginatePost.vue';

const posts = ref([])
const postForPage = 10;
const init = ref(0)
const end = ref(postForPage)
const favoritePostId = ref();
const isLoading = ref(true);

const handleClickButton = (id) => {
  favoritePostId.value = id;
}

const handlePagination = (direction) => {
  if (direction == 'prev') {
    init.value = init.value - postForPage
    end.value = end.value - postForPage;
    return;
  }
  init.value = init.value + postForPage;
  end.value = end.value + postForPage;
}

fetch('https://jsonplaceholder.typicode.com/posts').
then(res => res.json()).
then(data => posts.value = data).
catch(e => console.error(e)).
finally(() => {
  setTimeout(() => {
    isLoading.value = false
  }, 2*1000);
})

</script>

<template>

  <LoadingSpinnerVue v-if="isLoading" />
  <div class="container py-4" v-else>
    <h1 class="mb-2">Random Posts</h1>
    <h3>Mi Favorite post id is: {{ favoritePostId }}</h3>
    <PaginatePostVue
      @handlePagination="handlePagination"
      :disabledPrev="init == 0"
      :disabledNext="end == 100"
    />
    <BlogPost
      v-for="post in posts.slice(init, end)"
      :key="post.id"
      :body="post.body"
      :id="post.id"
      :title="post.id+ ' - ' + post.title"
      @handleClickButton="handleClickButton"
      ></BlogPost>
  </div>

</template>

<style>
  h1 {
    color: blue;
  }
</style>