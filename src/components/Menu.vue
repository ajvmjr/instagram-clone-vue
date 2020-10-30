<template>
  <div>
    <v-menu bottom offset-y>
      <template v-slot:activator="{ on, attrs }">
        <img
          alt="user profile pic"
          :src="getUser.avatar"
          v-bind="attrs"
          v-on="on"
        />
      </template>
      <v-list>
        <v-list-item dense>
          <v-list-item-icon>
            <v-icon>account_circle</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Perfil</v-list-item-title>
        </v-list-item>
        <v-list-item dense>
          <v-list-item-icon>
            <v-icon>bookmark_border</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Salvos</v-list-item-title>
        </v-list-item>
        <v-list-item dense>
          <v-list-item-icon>
            <v-icon>settings</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Configurações</v-list-item-title>
        </v-list-item>
        <v-list-item dense @click="logout">
          <v-list-item-title>Sair</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters(["getUser"]),
  },

  methods: {
    logout() {
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style lang="scss" scoped>
.v-app-bar {
  .v-avatar {
    cursor: pointer;
    img {
      height: 100%;
      object-fit: cover;
      width: 100%;
    }
  }
}
</style>
