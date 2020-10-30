<template>
  <div>
    <Header />
    <Stories />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Stories from "@/components/Stories";
import { mapGetters } from "vuex";

export default {
  data: () => ({
    user: {},
  }),

  components: {
    Header,
    Stories,
  },

  computed: {
    ...mapGetters(["getUser"]),
  },
};
</script>

<style lang="scss" scoped>
.test {
  display: flex;
}

.side-bar {
  background: red;
  width: 50%;
  height: 100%;
}
</style>
