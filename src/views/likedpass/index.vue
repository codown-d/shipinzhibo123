<template>
  <div class="margin-top-sm" v-for="item in list">
    <anchor-news
      :publisher="item.publisher"
      :text="item.text"
      :comment_count="item.comment_count"
      :like_count="item.like_count"
      :relay_count="item.relay_count"
      :liked="item.liked"
      :follow_status="item.follow_status"
      :ctime="item.ctime"
    ></anchor-news>
  </div>
</template>
<script setup>
import AnchorNews from "@/components/AnchorNews.vue";
import { onMounted, ref } from "vue";
import { getAnchorNews } from "@/api/chat";
let list = ref([]);
onMounted(() => {
  getAnchorNews().then((res) => {
    list.value = res.data.list;
  });
});
</script>
<style lang="sass" scoped></style>
