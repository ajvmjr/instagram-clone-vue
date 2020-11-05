<template>
  <v-card flat color="#fafafa" width="65%" class="sugestions">
    <div class="sugestions__header d-flex align-center">
      <v-card-title class="sugestions__header__title"
        >Sugestões para você</v-card-title
      >
      <v-spacer />
      <span>Ver tudo</span>
    </div>

    <v-card-text>
      <v-list class="sugestions__list">
        <v-list-item v-for="(sugestion, index) in sugestions" :key="index">
          <v-list-item-avatar>
            <v-avatar size="45">
              <img
                :src="sugestion.avatar"
                alt="foto de perfil do usuário sugerido"
              />
            </v-avatar>
          </v-list-item-avatar>
          <v-list-item-content>
            <span>{{ sugestion.name }}</span>
            <p>
              {{ followedBy(sugestion.followedBy) }}
            </p>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-card-text>
  </v-card>
</template>

<script>
import axios from "axios";

export default {
  data: () => ({
    sugestions: [],
    formatedMessage: "",
  }),

  mounted() {
    this.get();
    this.followedBy();
  },

  methods: {
    async get() {
      const { data } = await axios.get("http://localhost:3000/sugestions");
      this.sugestions = data;
    },

    followedBy(list) {
      return `Seguido por ${list[0]} e mais ${list.length - 1} pessoas`;
    },
  },
};
</script>

<style lang="scss" scoped>
.sugestions {
  &__header {
    &__title {
      color: #8e8e8e;
      font-size: 14px;
      font-weight: 500;
    }

    span {
      color: #262626;
      cursor: pointer;
      font-size: 12px;
      font-weight: 500;
      letter-spacing: 0.01em;
    }
  }

  &__list {
    padding: 0;
    .v-list-item {
      background: #fafafa;
    }

    img {
      height: 100%;
      object-fit: cover;
      width: 100%;
    }

    span {
      color: #262626;
      cursor: pointer;
      font-size: 14px;
      font-weight: 500;
    }

    p {
      color: #8e8e8e;
      font-size: 12px;
      font-weight: normal;
    }
  }
}
</style>
