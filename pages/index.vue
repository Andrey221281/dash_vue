<template>
  <div class="login">
    <div class="logo login__logo">
      <Logo />
    </div>
    <form @submit.prevent="hundleSubmit" class="login-form">
      <Input
        v-model="values.login"
        type="text"
        placeholder="Логин"
        class="mb-2"
      />
      <Input
        v-model="values.pass"
        type="text"
        placeholder="Пароль"
        class="mb-2"
      />
      <Button :disabled="!isValid" class="btn mt-1" block type="submit">
        Войти
      </Button>
    </form>
  </div>
</template>

<script>
import Logo from "../components/Logo";

import Input from "../components/Input";
import Button from "../components/Button";
export default {
  layout: "login",
  components: {
    Logo,
    Input,
    Button
  },
  data() {
    return {
      values: {
        login: null,
        pass: null
      }
    };
  },
  methods: {
    hundleSubmit: function(e) {
      this.$router.push("/dashboard");
    }
  },
  computed: {
    isValid() {
      if (this.values.login && this.values.pass) return true;
    }
  }
};
</script>

<style lang="scss">
@import "~/assets/scss/style.scss";
.login {
  width: 25rem;
}
.login__logo {
  width: 100%;
  margin-bottom: 2.5rem;
  & svg {
    display: block;
    margin: 0 auto;
  }
}
</style>
