<template>
  <Header />
  <section class="text-gray-600 body-font overflow-hidden">
    <div class="container px-5 py-24 mx-auto">
      <div class="lg:w-4/5 mx-auto flex flex-wrap">
        <img
          alt="ecommerce"
          class="w-80 h-43 object-cover object-center rounded"
          :src="post[0].image"
        />
        <div class="lg:w-1/2 w-full lg:pl-10 lg:py-6 mt-6 lg:mt-0">
          <h2 class="text-sm title-font text-gray-500 tracking-widest">
            Name Book
          </h2>
          <h1 class="text-gray-900 text-3xl title-font font-medium mb-1">
            {{ post[0].title }}
          </h1>
          <div class="flex mb-4">
            <span class="flex items-center">
              <svg
                fill="currentColor"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                class="w-4 h-4 text-red-500"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
                ></path>
              </svg>

              <span class="text-gray-600 ml-3">4 Reviews</span>
            </span>
            <span
              class="flex ml-3 pl-3 py-2 border-l-2 border-gray-200 space-x-2s"
            >
            </span>
          </div>
          <p class="leading-relaxed">{{ post[0].description }}</p>
          <span class="title-font font-medium text-2xl text-gray-900"
            >${{ post[0].price }}</span
          >

          <NuxtLink :to="`reservation-${post[0].id}`">
            <button
              class="flex ml-auto text-white bg-red-500 border-0 py-2 px-6 focus:outline-none hover:bg-red-600 rounded"
            >
              reservation
            </button>
          </NuxtLink>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const headers = {
  apikey:
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c",
};

const route = useRoute();

const { pending, data: post } = await useFetch(
  `https://vwdufkxcsvsywmjjbffm.supabase.co/rest/v1/books?id=eq.${route.params.id}&select=*`,
  { headers: headers }
);

console.log(post);
</script>
