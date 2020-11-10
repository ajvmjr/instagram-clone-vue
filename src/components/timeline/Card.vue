<template>
  <div>
    <v-card width="614" class="card mt-10" outlined>
      <div class="card__user-info">
        <v-card-title>
          <v-avatar size="40" color="primary">
            <img :src="post.avatar" alt="foto de perfil do usuário" />
          </v-avatar>
        </v-card-title>
        <div class="card__user-info card__user-info--name-location">
          <span>{{ post.author }}</span>
          <p>{{ post.location }}</p>
        </div>
      </div>
      <!-- <v-btn fab icon class="card__more-options">
        <v-icon>more_horizontal</v-icon>
      </v-btn> -->

      <img
        :src="post.image"
        alt="imagem do post"
        class="card card--post-image"
      />

      <v-card-actions class="card__actions">
        <div>
          <v-icon size="30">favorite_border</v-icon>
          <v-icon size="30">chat_bubble_outline</v-icon>
          <v-icon size="30">near_me</v-icon>
        </div>
        <v-icon size="30">bookmark_border</v-icon>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  props: {
    post: Object,
  },
};
</script>

<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  position: relative;
  &__user-info {
    display: flex;
    // background: yellow;
    width: 65%;

    &--name-location {
      justify-content: center;
      display: flex;
      flex-direction: column;
      // background: red;
      padding-top: 10px;

      span {
        font-size: 14px;
        font-weight: 500;
        text-transform: lowercase;
      }

      p {
        font-size: 12px;
        font-weight: normal;
      }

      img {
        height: 100%;
        object-fit: cover;
        width: 100%;
      }
    }
  }

  &--post-image {
    width: 614px;
  }

  &__actions {
    align-items: center;
    display: flex;
    justify-content: space-between;
    width: 100%;

    div {
      display: flex;
      justify-content: space-between;
      width: 150px;
    }
  }

  &__more-options {
    position: fixed;
    right: 0;
  }
}
</style>
