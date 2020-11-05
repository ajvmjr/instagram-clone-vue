<template>
  <div style="background: #FAFAFA">
    <Header />
    <div class="spacer d-flex">
      <section class="spacer spacer--left">
        <StoriesCard />
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
import Header from "@/components/Header";
import StoriesCard from "@/components/timeline/StoriesCard";
import Sugestions from "@/components/timeline/Sugestions";

import { mapGetters } from "vuex";

export default {
  data: () => ({
    user: {},
  }),

  components: {
    Header,
    StoriesCard,
    Sugestions,
  },

  computed: {
    ...mapGetters(["getUser"]),
  },
};
</script>

<style lang="scss" scoped>
.spacer {
  height: 100vh;
  width: 100vw;
  &--left {
    // background: green;
    display: flex;
    justify-content: flex-end;
    padding-top: 90px;
    width: 60%;
  }
  &--right {
    display: flex;
    // background: red;
    flex-direction: column;
    padding: 110px 0 0 40px;
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
