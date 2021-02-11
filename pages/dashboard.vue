<template>
  <div class="dashboard">
    <h1 class="dashboard__title">Мой профиль</h1>
    <div class="dashboard__content">
      <div class="dashboard__form">
        <form @submit.prevent="hundleSubmit">
          <div class="dashboard__form-box">
            <div class="dashboard__input-box">
              <Input
                variant="underline small"
                type="text"
                label="Имя"
                v-model="values.name"
                required
                errMessage="Пожалуйста заполните поле Имя"
                :isSubmited="isSubmited"
              />

              <Input
                variant="underline small"
                type="text"
                label="Фамилия"
                v-model="values.secondName"
                required
                errMessage="Пожалуйста заполните поле Фамилия"
                :isSubmited="isSubmited"
              />
            </div>
            <div class="dashboard__input-box">
              <Input
                variant="underline small"
                small
                type="text"
                label="Сменить пароль"
                v-model="values.updatePass"
                required
                errMessage="Пожалуйста заполните поле пароль"
                :isSubmited="isSubmited"
              />

              <Input
                variant="underline small"
                small
                type="text"
                label="Сменить логин"
                v-model="values.updateLogin"
                required
                errMessage="Пожалуйста заполните поле логин"
                :isSubmited="isSubmited"
              />
            </div>
          </div>
          <div style="text-align: right">
            <Button class="btn mt-2" type="submit">
              Сохранить
            </Button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "../components/Button";
import Input from "../components/Input";

export default {
  components: {
    Button,
    Input
  },
  data() {
    return {
      isSubmited: false,
      values: {
        name: "",
        secondName: "",
        updatePass: "",
        updateLogin: ""
      }
    };
  },
  methods: {
    hundleSubmit(e) {
      this.isSubmited = true;
      console.log({ values: this.values });
    }
  }
};
</script>

<style lang="scss">
@import "~/assets/scss/style.scss";
.dashboard {
  padding: $space-xl;
  &__content {
    background: $white;
    padding: $space-xl;
    border-radius: $radius-base;
  }
  &__form-box {
    display: flex;

    @media (max-width: 1200px) {
      flex-direction: column;
    }
  }
  &__input-box {
    flex: 1;

    &:first-child * {
      padding-right: $space-xl;
      @media (max-width: 1200px) {
        padding-right: 0;
      }
    }
  }
}
</style>
