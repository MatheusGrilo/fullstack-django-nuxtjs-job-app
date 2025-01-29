<template>
  <div class="py-10 px-6">
    <h1 class="mb-6 text-2xl font-semibold">Create Job</h1>

    <form class="space-y-4">
      <div>
        <label>Category</label>
        <select
          class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
        >
          <option value="">Select category</option>
          <option value="">Select category 1</option>
          <option value="">Select category 2</option>
        </select>
      </div>

      <div>
        <label>Title</label>
        <input
          type="text"
          class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
        />
      </div>

      <div>
        <label>Description</label>
        <textarea
          class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
        />
      </div>

      <div>
        <label>Location</label>
        <input
          type="text"
          class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
        />
      </div>

      <div>
        <label>Salary</label>
        <input
          type="text"
          class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
        />
      </div>

      <div>
        <label>Company name</label>
        <input
          type="text"
          class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
        />

        <div>
          <label>Company location</label>
          <input
            type="text"
            class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
          />
        </div>

        <div>
          <label>Company email</label>
          <input
            type="text"
            class="w-full mt-2 p-4 rounded-xl bg-gray-100 text-black dark:bg-gray-800 dark:text-white"
          />
        </div>
      </div>

      <button class="py-4 px-6 bg-fuchsia-700 text-white rounded-xl">
        Submit
      </button>
    </form>
  </div>
</template>
