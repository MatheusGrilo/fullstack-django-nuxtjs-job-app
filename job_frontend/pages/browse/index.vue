<script setup>
// Categories
let { data: jobCategories } = await useFetch(
  "http://localhost:8000/api/v1/jobs/categories"
);
let selectedCategoriesRef = ref("");
let selectedCategories = [];

function toggleCategory(id) {
  const index = selectedCategories.indexOf(id);

  if (index === -1) {
    selectedCategories.push(id);
  } else {
    selectedCategories.splice(index, 1);
  }

  selectedCategoriesRef.value = selectedCategories.join(",");
}

// Jobs
let { data: jobs } = await useFetch("http://localhost:8000/api/v1/jobs", {
  query: { categories: selectedCategoriesRef },
});
</script>

<template>
  <div class="grid md:grid-cols-4 gap-3 py-10 px-6">
    <div class="md:col-span-1 px-6 py-6 bg-fuchsia-700 rounded-xl">
      <div class="flex space-x-4">
        <input
          type="search"
          placeholder="Find your next job..."
          class="w-full px-6 py-4 rounded-xl"
        />
        <button class="py-4 px-6 bg-fuchsia-900 text-white rounded-xl">
          <Icon name="mdi:magnify" class="size-6 mt-1" />
        </button>
      </div>

      <hr class="my-6 opacity-30" />

      <h3 class="mt-6 text-xl text-white">Categories</h3>
      <div class="mt-6 space-y-4">
        <p
          v-for="category in jobCategories"
          v-on:click="toggleCategory(category.id)"
          vf-bind:key="category.id"
          class="py-4 px-6 text-white rounded-xl"
          v-bind:class="{
            'bg-fuchsia-900': selectedCategoriesRef.includes(category.id),
          }"
        >
          {{ category.title }}
        </p>
      </div>
    </div>

    <div class="md:col-span-3">
      <div class="space-y-4">
        <Job v-for="job in jobs" :key="job.id" :job="job" />
      </div>
    </div>
  </div>
</template>
