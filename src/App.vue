<template>
  <m-header></m-header>
  <tab></tab>
  <router-view :style="viewStyle" v-slot="{ Component }">
    <keep-alive>
      <component :is="Component" />
    </keep-alive>
  </router-view>
  <player></player>
</template>

<script>
import Header from "@/components/header/header.vue";
import Tab from "@/components/tab";
import Player from "@/components/player/player.vue";
import { mapState } from "vuex";
export default {
  components: {
    MHeader: Header,
    Tab,
    Player,
  },
  computed: {
    viewStyle() {
      const bottom = this.playList.length ? "60px" : "0";
      return {
        bottom,
      };
    },
    ...mapState(["playList"]),
  },
};
</script>

<style></style>
