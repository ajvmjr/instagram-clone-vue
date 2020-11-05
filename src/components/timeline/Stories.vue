<template>
  <div>
    <v-avatar size="58" class="mt-4">
      <img
        :src="storieInfo.avatar"
        alt="imagem do usuário que postou o storie"
      />
    </v-avatar>
    <p>{{ storieInfo.name }}</p>
  </div>
</template>

<script>
export default {
  props: {
    storieInfo: Object,
  },
};
</script>

<style lang="scss" scoped>
img {
  height: 100%;
  object-fit: cover;
  width: 100%;
}

p {
  margin-top: 5px;
  font-size: 12px;
}
</style>
