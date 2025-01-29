<script setup>
const router = useRouter();

let username = ref("");
let email = ref("");
let password1 = ref("");
let password2 = ref("");
let errors = ref([]);

async function submitForm() {
  console.log("submitForm");
  errors.value = [];

  await $fetch("http://localhost:8000/api/v1/users/", {
    method: "POST",
    body: {
      username: username.value,
      email: email.value,
      password: password1.value,
    },
  })
    .then((response) => {
      console.log("response", response);

      router.push({ path: "/login" });
    })
    .catch((error) => {
      if (error.response) {
        for (const property in error.response._data) {
          errors.value.push(`${property}: ${error.response._data[property]}`);
        }
      } else if (error.message) {
        errors.value.push("Something went wrong. Please, try again later.");

        console.log(JSON.stringify(error));
      }
    });
}
</script>

<template>
  <div class="py-10 px-6">
    <div
      class="max-w-sm mx-auto py-10 px-6 bg-gray-100 dark:bg-gray-800 rounded-xl"
    >
      <h1 class="mb-6 text-2xl text-black dark:text-white">Sign up</h1>
      <form v-on:submit.prevent="submitForm">
        <input
          v-model="username"
          type="username"
          placeholder="your_username"
          class="w-full mb-4 py-4 px-6 rounded-xl"
        />
        <input
          v-model="email"
          type="email"
          placeholder="your@email.com"
          class="w-full mb-4 py-4 px-6 rounded-xl"
        />
        <input
          v-model="password1"
          type="password"
          placeholder="Password"
          class="w-full mb-4 py-4 px-6 rounded-xl"
        />
        <input
          v-model="password2"
          type="password"
          placeholder="Repeat password"
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
          Create account
        </button>
      </form>
    </div>
  </div>
</template>
