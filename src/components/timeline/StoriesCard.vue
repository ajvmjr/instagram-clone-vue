<template>
  <div>
    <v-card
      outlined
      width="614px"
      height="120px"
      class="d-flex align-center justify-space-around"
    >
      <Stories
        v-for="(storie, index) in storiesList"
        :key="index"
        :storieInfo="storie"
      />
    </v-card>
  </div>
</template>

<script>
import axios from "axios";
import Stories from "@/components/timeline/Stories";
export default {
  data: () => ({
    storiesList: [],
  }),

  components: { Stories },

  mounted() {
    this.getStories();
  },

  methods: {
    async getStories() {
      const { data } = await axios.get("http://localhost:3000/stories");
      this.storiesList = data;
    },
  },
};
</script>

<style lang="scss" scoped>
.v-card {
  overflow-y: hidden;
  overflow-x: auto;
}
</style>
