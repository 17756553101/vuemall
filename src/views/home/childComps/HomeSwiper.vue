<template>
  <swiper>
    <swiper-item v-for="(item, index) in banners" :key="index">
      <a :href="item.link">
        <img :src="item.image" alt="" />
      </a>
    </swiper-item>
  </swiper>
</template>

<script>
import { Swiper } from "../../../components/common/swiper";
import { SwiperItem } from "../../../components/common/swiper";

export default {
  name: "WorkspaceJsonHomeswiper",
  props: {
    banners: {
      type: Array,
      defalut() {
        return [];
      },
    },
  },
  components: {
    Swiper,
    SwiperItem,
  },
  data() {
    return {};
  },

  mounted() {},

  methods: {},
};
</script>

<style  scoped>
</style>