<template>
  <div>
    <v-footer class="d-flex align-center justify-space-evenly">
      <div class="d-flex justify-center links">
        <a href="#" class="anchor">sobre</a>
        <a href="#" class="anchor">ajuda</a>
        <a href="#" class="anchor">imprensa</a>
        <a href="#" class="anchor">api</a>
        <a href="#" class="anchor">carreiras</a>
        <a href="#" class="anchor">privacidade</a>
        <a href="#" class="anchor">termos</a>
        <a href="#" class="anchor">localizações</a>
        <a href="#" class="anchor">contas mais relevantes</a>
        <a href="#" class="anchor">hashtags</a>
        <a href="#" class="anchor">idioma</a>
      </div>
      <span>© 2020 instagram do facebook</span>
    </v-footer>
  </div>
</template>

<style lang="scss" scoped>
.v-footer {
  height: 80px;
  width: 100%;
  .links {
    width: 80%;
    .anchor {
      color: #00376b;
      font-size: 12px;
      font-weight: 500;
      padding: 0 10px;
      text-decoration: none;
      text-transform: uppercase;
    }
  }

  span {
    color: #8e8e8e;
    font-size: 12px;
    text-transform: uppercase;
  }
}
</style>
