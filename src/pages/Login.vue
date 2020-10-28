<template>
  <div style="background: #FAFAFA">
    <v-container class="d-flex align-center justify-center v-container">
      <section>
        <img src="@/assets/left-img-login.png" alt="" />
      </section>
      <section class="v-container__cards">
        <v-card
          class="d-flex flex-column align-center ml-5 v-container__cards__login"
          outlined
          tile
        >
          <v-card-title class="mb-8 v-container__cards__login__title"
            >Instagram</v-card-title
          >

          <v-form @submit="login">
            <div>
              <v-text-field
                background-color="#fafafa"
                type="email"
                filled
                dense
                outlined
                label="Telefone, nome de usuário ou email"
                v-model="email"
              ></v-text-field>
              <v-text-field
                background-color="#fafafa"
                filled
                dense
                outlined
                label="Senha"
                type="password"
                v-model="password"
              >
              </v-text-field>
            </div>
            <v-btn
              color="#0095f6"
              class="mt-2"
              block
              elevation="0"
              type="submit"
              :loading="buttonLoading"
              >Entrar</v-btn
            >
          </v-form>
          <h3>ou</h3>
          <div class="d-flex">
            <v-icon class="mr-2 mt-4" color="#385185">facebook</v-icon>
            <h4>Entrar com facebook</h4>
          </div>
          <span v-show="showConfirm">
            Usuário ou senha incorretos.
          </span>
          <a>Esqueceu a senha?</a>
        </v-card>
        <v-card
          class="d-flex align-center justify-center mt-5 ml-5 v-container__cards__register"
          outlined
          tile
        >
          <p>Não tem uma conta? <a href="#">Cadastre-se</a></p>
        </v-card>
      </section>
    </v-container>
    <Footer />
  </div>
</template>

<script>
import axios from "axios";
import Footer from "@/components/Footer";

export default {
  data: () => ({
    email: "",
    password: "",
    responseStatus: "",
    passwordWasEntered: false,
    buttonLoading: false,
    showConfirm: false,
  }),

  components: {
    Footer,
  },

  watch: {
    responseStatus() {
      const { responseStatus } = this;
      if (responseStatus) {
        this.buttonLoading = false;
        return;
      }
    },
  },

  methods: {
    async login(e) {
      e.preventDefault();
      this.startButtonLoading();

      const { email, password } = this;

      await axios
        .get(`http://localhost:3000/users?email=${email}&password=${password}`)
        .then((res) => {
          this.responseStatus = res.status;
          const data = res.data;
          if (this.validUser(data)) {
            this.$store.dispatch("setUser", data[0]);
            this.$router.push({ name: "Timeline" });
          } else {
            this.showConfirm = true;
          }
        })
        .catch((err) => console.log(err));
    },

    validUser(data) {
      return data.length > 0 ? true : false;
    },

    startButtonLoading() {
      this.buttonLoading = true;
    },
  },
};
</script>

<style lang="scss" scoped>
.v-container {
  background: #fafafa;
  height: 100vh;
  width: 100%;
  &__cards {
    width: 40%;

    &__login {
      height: 90%;
      background: #fff;
      width: 75%;
      &__title {
        color: #262626;
        font-size: 40px;
        font-family: "Pacifico", cursive;
      }
      .v-form {
        width: 85%;
        div {
          .v-text-field {
            font-size: 12px;
          }
        }
        .v-btn {
          text-transform: none;
          color: white;
        }
      }

      h3 {
        color: #8e8e8e;
        font-size: 18px;
        font-weight: normal;
        margin-top: 20px;
        text-align: center;
        width: 72%;
        &:before,
        &:after {
          background-color: #8e8e8e;
          content: "";
          display: inline-block;
          height: 1px;
          position: relative;
          vertical-align: middle;
          width: 50%;
        }

        &:before {
          right: 0.5em;
          margin-left: -50%;
        }

        &:after {
          left: 0.5em;
          margin-right: -50%;
        }
      }

      h4 {
        color: #385185;
        font-size: 14px;
        font-weight: 500;
        letter-spacing: 0.5px;
        padding-top: 20px;
      }

      span {
        color: #ed4956;
        font-size: 14px;
        margin-top: 20px;
        font-weight: 400;
      }

      a {
        color: rgb(66, 62, 62);
        text-decoration: none;
        font-size: 12px;
        line-height: 14px;
        margin-top: 25px;
        margin-bottom: 15px;
      }
    }
    &__register {
      background: #fff;
      height: 65px;
      padding-top: 12px;
      width: 75%;
      p {
        color: rgb(66, 62, 62);
        font-weight: 300;
        font-size: 14px;
      }
      a {
        font-weight: 500;
        text-decoration: none;
      }
    }
  }
}
</style>
