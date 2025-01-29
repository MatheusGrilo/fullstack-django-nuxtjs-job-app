<template>
  <div>
    <nav class="p-6 flex items-center justify-between bg-fuchsia-800">
      <NuxtLink to="/" class="text-2xl font-bold text-white"
        >Fullstack Job</NuxtLink
      >
      <div class="flex items-center space-x-4">
        <NuxtLink to="/" class="text-white hover:text-fuchsia-300"
          >Home</NuxtLink
        >
        <NuxtLink to="/browse" class="text-white hover:text-fuchsia-300"
          >Browse</NuxtLink
        >
      </div>
    </nav>

    <slot />

    <footer class="p-6 flex flex-wrap items-center justify-between bg-gray-900">
      <p class="text-gray-300">© 2025 Fullstack Job</p>

      <div class="flex mt-6 md:mt-0 items-center space-x-4">
        <NuxtLink
          to="/login"
          class="py-4 px-6 bg-fuchsia-900 hover:bg-fuchsia-700 text-white rounded-xl"
          >Login</NuxtLink
        >
        <NuxtLink
          to="/signup"
          class="py-4 px-6 bg-fuchsia-600 hover:bg-fuchsia-700 text-white rounded-xl"
          >Signup</NuxtLink
        >
      </div>
    </footer>
  </div>
</template>
