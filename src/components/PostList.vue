<!--
 * @Author: your name
 * @Date: 2020-12-07 16:09:53
 * @LastEditTime: 2020-12-11 10:32:35
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \my-zhehu\src\components\PostList.vue
-->
<template>
  <div class="post-list">
    <article v-for="post in posts" :key="post._id" class="card mb-3 shadow0sm">
      <div class="card-body">
        <h4>
          <router-link to="/">{{ post.title }}</router-link>
        </h4>
        <div class="row my-3 aligin-items-center">
          <div class="col-4" v-if="post.image">
            <img class="rounded-lg w-100" :src="post.image.url" :alt="post.title" />
          </div>
          <p :class="{ 'col-8': post.image }" class="text-muted">{{ post.excrept }}</p>
        </div>
        <span class="text-muted">{{ post.createdAt }}</span>
      </div>
    </article>
  </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import { PostProps } from "@/store";
export default defineComponent({
  name: "PostList",
  props: {
    list: {
      required: true,
      type: Array as PropType<PostProps[]>,
    },
  },
  setup(props) {
    console.log("PostList", props.list);
    const posts = computed(() => props.list);
    return {
      posts,
    };
  },
});
</script>
