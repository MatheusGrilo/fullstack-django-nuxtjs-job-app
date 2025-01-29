<script>
import { useUserStore } from "@/stores/user";
import { useRouter } from "vue-router";

export default {
  setup() {
    const router = useRouter();
    const userStore = useUserStore();

    let username = ref("");
    let password = ref("");

    let errors = ref([]);

    async function submitForm() {
      errors.value = [];

      await $fetch("http://localhost:8000/api/v1/token/login/", {
        method: "POST",
        body: {
          username: username.value,
          password: password.value,
        },
      })
        .then((data) => {
          console.log("response", data.auth_token);

          userStore.setToken(data.auth_token, username.value);

          router.push({ path: "/" });
        })
        .catch((error) => {
          if (error.response) {
            for (const property in error.response._data) {
              errors.value.push(
                `${property}: ${error.response._data[property]}`
              );
            }
          } else if (error.message) {
            errors.value.push("Something went wrong. Please, try again later.");

            console.log(JSON.stringify(error));
          }
        });
    }

    return {
      username,
      password,
      errors,
      submitForm,
    };
  },
};
</script>

<template>
  <div class="py-10 px-6">
    <div
      class="max-w-sm mx-auto py-10 px-6 bg-gray-100 dark:bg-gray-800 rounded-xl"
    >
      <h1 class="mb-6 text-2xl text-black dark:text-white">Log in</h1>
      <form v-on:submit.prevent="submitForm">
        <input
          v-model="username"
          type="text"
          placeholder="your_username"
          class="w-full mb-4 py-4 px-6 rounded-xl"
        />
        <input
          v-model="password"
          type="password"
          placeholder="Password"
          class="w-full mb-4 py-4 px-6 rounded-xl"
        />

        <div
          v-if="errors.length"
          class="mb-6 py-4 px-6 bg-rose-700 text-white rounded-xl"
        >
          <p v-for="error in errors" v-bind:key="error" class="mb-2">
            {{ error }}
          </p>
        </div>

        <button class="py-4 px-6 bg-fuchsia-700 text-white rounded-xl w-full">
          Submit
        </button>
      </form>
    </div>
  </div>
</template>
