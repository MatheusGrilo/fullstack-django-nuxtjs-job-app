<template>
  <div class="py-10 px-6 grid md:grid-cols-4 gap-3">
    <div class="md:col-span-3">
      <h1 class="mb-6 text-3xl">Title</h1>

      <p>Job description</p>
      <NuxtLink
        to="#"
        class="inline-block mt-6 py-4 px-6 bg-fuchsia-700 text-white rounded-xl"
        >Apply</NuxtLink
      >
    </div>

    <div class="md:col-span-1 p-6 bg-fuchsia-700 text-white rounded-xl">
      <h3 class="mb-6 text-2xl">Company</h3>
      <p class="mb-2">Company name</p>

      <hr class="my-6 opacity-30" />

      <h3 class="mb-6 text-2xl">Position</h3>
      <p class="mb-2">Position location</p>
      <p>Salary range</p>

      <hr class="my-6 opacity-30" />

      <p>Posted at Dec. 1 2022</p>
    </div>
  </div>
</template>
