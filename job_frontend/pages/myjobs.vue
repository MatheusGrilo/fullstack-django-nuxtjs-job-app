<script setup>
import { onMounted, ref } from "vue";
import { useRouter } from "vue-router";
import { useUserStore } from "@/stores/user";

const userStore = useUserStore();
const router = useRouter();
let jobs = ref([]);

onMounted(() => {
  if (!userStore.user.isAuthenticated) {
    router.push({ path: "/login" });
  } else {
    getJobs();
    console.log("User is authenticated");
  }
});

async function getJobs() {
  await $fetch("http://localhost:8000/api/v1/jobs/my", {
    headers: {
      Authorization: `token ${userStore.user.token}`,
      "Content-Type": "application/json",
    },
  })
    .then((response) => {
      jobs.value = response;
    })
    .catch((error) => {
      console.log("error: ", error);
    });
}
</script>

<template>
  <div class="py-10 px-6">
    <h1 class="mb-6 text-2xl font-semibold">My jobs</h1>

    <div class="space-y-4">
      <Job v-for="job in jobs" :key="job.id" :job="job" my />
    </div>
  </div>
</template>
