<template>
  <div>
    <v-app-bar
      absolute
      color="white"
      elevation="1"
      outlined
      height="54px"
      fixed
    >
      <v-spacer />
      <v-toolbar-title>
        <h1 class="header-title">Instagram</h1>
      </v-toolbar-title>

      <v-spacer />
      <div class="input-query">
        <v-text-field
          prepend-inner-icon="mdi-magnify"
          placeholder="Pesquisar"
          class="pt-5"
          solo
          dense
          flat
          outlined
          background-color="#fafafa"
        >
        </v-text-field>
      </div>

      <v-spacer />

      <v-btn icon>
        <v-icon>home</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>near_me</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>explore</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>favorite_border</v-icon>
      </v-btn>
      <v-avatar size="23">
        <Menu />
      </v-avatar>
      <v-spacer />
    </v-app-bar>
  </div>
</template>

<script>
import Menu from "@/components/Menu";

export default {
  components: {
    Menu,
  },
};
</script>

<style lang="scss" scoped>
$text-field-border-radius: 0 !default;

h1 {
  font-family: "Lobster", cursive;
  font-size: 25px;
}

.v-app-bar {
  .input-query {
    height: 50;
    .v-text-field {
      font-size: 14px;
      border-radius: $text-field-border-radius;
    }
  }
}
</style>
