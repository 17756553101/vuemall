<template>
  <div class="recommend">
    <div v-for="(item, index) in recommends" :key="index">
      <a :href="item.link">
        <img :src="item.image" alt="" />
        <div class="title">{{ item.title }}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "WorkspaceJsonRecommendview",
  props: {
    recommends: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return {};
  },

  mounted() {},

  methods: {},
};
</script>

<style scoped>
.recommend {
  display: flex;
  margin-top: 10px;
  font-size: 14px;

  padding-bottom: 30px;
  border-bottom: 10px solid #eee;
}

.recommend-item {
  flex: 1;
  text-align: center;

  /* margin-left: 8px; */
}

.recommend img {
  width: 79%;
  height: 72%;

  margin-bottom: 10px;
}
.title {
  margin-left: 10px;
}
</style>