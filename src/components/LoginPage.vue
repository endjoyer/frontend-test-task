<template>
  <div class="login-page">
    <h1>Войти в панель</h1>
    <input type="text" placeholder="Введите логин" v-model="username" />
    <input type="password" placeholder="Введите пароль" v-model="password" />
    <button @click="login">Войти</button>
  </div>
</template>

<script>
import { ref } from "vue";
import { useRouter } from "vue-router";
import { useStore } from "vuex";

export default {
  setup() {
    const username = ref("");
    const password = ref("");
    const router = useRouter();
    const store = useStore();

    const login = () => {
      if (username.value && password.value) {
        store.dispatch("login", username.value);
        router.push("/dashboard");
      } else {
        alert("Введите логин и пароль");
      }
    };

    return {
      username,
      password,
      login,
    };
  },
};
</script>

<style scoped lang="scss">
.login-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  h1 {
    font-size: 16px;
    font-weight: 500;
    margin: 0 0 30px;
  }
  input {
    box-sizing: border-box;
    width: 230px;
    margin: 0 0 10px;
    padding: 8px;
    border: 1px solid #d7d7d7;
    border-radius: 8px;
    font-size: 12px;
    font-weight: 400;
  }
  button {
    background-color: #000;
    color: #d7d7d7;
    padding: 8px 16px;
    border-radius: 8px;
    cursor: pointer;
    margin-top: 30px;
    font-size: 12px;
    font-weight: 400;
  }
}
</style>
