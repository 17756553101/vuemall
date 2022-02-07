<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners" />
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
    <tab-control
      class="tab-control"
      :titles="['流行', '新款', '精选']"
      @tabClick="tabClick"
    ></tab-control>
    <goods-list :goods="goods[this.activeGoods].list"></goods-list>
    <ul>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
      <li>10</li>
    </ul>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "./childComps/HomeSwiper.vue";
import RecommendView from "./childComps/RecommendView.vue";
import FeatureView from "./childComps/FeatureView.vue";
import GoodsList from "components/content/goods/GoodsList.vue";
import TabControl from "../../components/content/tabControl/TabControl.vue";

import { getHomeMultidata, getHomeGoods } from "../../network/home";

// import { Swiper } from "../../components/common/swiper";
// import { SwiperItem } from "../../components/common/swiper";

export default {
  name: "WorkspaceJsonHome",
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabControl,
    GoodsList,
    GoodsList,
  },
  data() {
    return {
      activeGoods: "pop",
      banners: [],
      recommends: [],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] },
      },
    };
  },
  created() {
    //1.请求多个数据
    this.getHomeMultidata();

    //2.请求商品数据
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
  },
  mounted() {},

  methods: {
    /*
事件监听
*/
    tabClick(index) {
      console.log(index);
      if (index == 1) {
        this.activeGoods = "new";
      }
      if (index == 2) {
        this.activeGoods = "sell";
      }
      if (index == 0) {
        this.activeGoods = "pop";
      }
    },
    /*
    网络请求
    */
    getHomeMultidata() {
      getHomeMultidata().then((res) => {
        console.log(res);
        this.banners = res.data.data.banner.list;
        this.recommends = res.data.data.recommend.list;
      });
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page).then((res) => {
        console.log(res);
        this.goods[type].list.push(...res.data.data.list);
        this.goods[type].page += 1;
      });
    },
  },
};
</script>

<style  scoped>
#home {
  padding-top: 44px;
}
.home-nav {
  background-color: var(--color-tint);
  color: aliceblue;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
.tab-control {
  position: sticky;
  top: 44px;
  z-index: 9;
}
</style>