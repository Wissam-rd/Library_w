<template>
  <Header />
  <span class="flex font-sans text-2xl rounded-full items-center justify-center"
    >Philosophical</span
  >
  <div class="gap-3 flex self-center bg-gray-100">
    <Sidebar />

    <div class="relative grid grid-cols-5 gap-6 col-md-12 mb-4">
      <div
        v-for="post in posts"
        class="grid max-w-lg overflow-hidden bg-white rounded-xl px-3 py-5 mt-3 shadow-xl dark:bg-black"
      >
        <div class="px-4 py-2">
          <!-- <p class="mt-1 text-sm text-gray-600 dark:text-gray-400">{{ post.description}}</p> -->
        </div>
        <img
          class="object-cover w-full max-h-72 h-full rounded-md mt-2"
          :src="post.image"
          alt="NIKE AIR"
        />
        <h1
          class="py-3 flex items-center justify-center border-solid-4 text-black mt-auto text-lg font-semibold"
        >
          {{ post.title }}
        </h1>
        <div
          class="flex items-center justify-between px-4 py-5 rounded-md bg-gray-900"
        >
          <h1 class="text-lg font-bold text-white">${{ post.price }}</h1>
          <NuxtLink :to="`card-${post.id}`">
            <button
              class="px-2 py-1 text-xs font-semibold text-gray-900 uppercase transition-colors duration-300 transform bg-white rounded-full hover:bg-gray-200 focus:bg-gray-400 focus:outline-none"
            >
              reservation
            </button></NuxtLink
          >
        </div>
      </div>
      <div></div>
    </div>
  </div>
</template>
<script setup>
const headers = {
  apikey:
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c",
};

const { pending, data: posts } = await useFetch(
  "https://vwdufkxcsvsywmjjbffm.supabase.co/rest/v1/books?type=eq.philosophical&select=*",
  { headers: headers }
);

console.log(posts);
</script>
