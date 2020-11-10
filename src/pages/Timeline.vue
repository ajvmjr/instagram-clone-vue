<template>
  <div style="background: #FAFAFA;">
    <Header />
    <div class="spacer d-flex">
      <section class="spacer spacer--left">
        <StoriesCard />
        <Card v-for="(post, index) in posts" :key="index" :post="post" />
      </section>
      <section class="spacer spacer--right">
        <div class="spacer__user-info">
          <v-avatar size="58" color="primary">
            <img :src="getUser.avatar" alt="foto de perfil do usuário" />
          </v-avatar>
          <span>{{ getUser.name }}</span>
        </div>

        <Sugestions />
      </section>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import Header from "@/components/Header";
import Card from "@/components/timeline/Card";
import StoriesCard from "@/components/timeline/StoriesCard";
import Sugestions from "@/components/timeline/Sugestions";

import { mapGetters } from "vuex";

export default {
  data: () => ({
    user: {},
    posts: [],
  }),

  components: {
    Header,
    Card,
    StoriesCard,
    Sugestions,
  },

  computed: {
    ...mapGetters(["getUser"]),
  },

  mounted() {
    this.getPosts();
  },

  watch: {
    posts() {
      console.log(this.posts);
    },
  },

  methods: {
    async getPosts() {
      const { data } = await axios.get("http://localhost:3000/posts");
      this.posts = data;
    },
  },
};
</script>

<style lang="scss" scoped>
.spacer {
  height: 100vh;
  position: relative;
  width: 100vw;
  &--left {
    align-items: flex-end;
    display: flex;
    flex-direction: column;
    padding-top: 90px;
    width: 60%;
  }
  &--right {
    display: flex;
    // background: red;
    flex-direction: column;
    padding: 110px 0 0 40px;
    // position: fixed;
    width: 40%;
  }

  &__user-info {
    display: flex;
    // background: yellow;
    height: 12%;
    width: 65%;

    span {
      padding: 18px;
      font-size: 14px;
      font-weight: 500;
      text-transform: lowercase;
    }

    img {
      height: 100%;
      object-fit: cover;
      width: 100%;
    }
  }
}
</style>
