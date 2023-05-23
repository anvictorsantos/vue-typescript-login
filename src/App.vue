<template>
  <div v-if="!userStore.getters.isLoggedIn" class="d-grid gap-2 col-6 mx-auto">
    <FormLogin />
  </div>
  <div v-else class="text-center">
    <h2>Welcome, {{ userStore.state.name }}</h2>
    <CounterNumbers />
    <button class="btn btn-secondary" @click="userStore.logout()">
      Logout
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue';
import FormLogin from './components/FormLogin.vue';
import CounterNumbers from './components/CounterNumbers.vue';
import userStore from './stores/user';

export default defineComponent({
  name: 'App',
  components: { FormLogin, CounterNumbers },
  setup() {
    onMounted(userStore.getUser)
    return { userStore }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
