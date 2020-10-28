<template>
  <div>
    <h1>Bem vindo {{ getUser.name }}</h1>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  data: () => ({
    user: {},
  }),

  computed: {
    ...mapGetters(["getUser"]),
  },
};
</script>
