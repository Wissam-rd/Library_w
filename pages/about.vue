<template>
    <!-- <Header/> -->

  <div>
    <section class="text-gray-600 body-font">
      <div
        class="container mx-auto flex px-5 py-2 md:flex-row flex-col items-center"
      >
        <div class="lg:max-w-lg lg:w-full md:w-1/2 w-5/6 mb-10 md:mb-0">
          <img
            class="object-cover object-center rounded"
            alt="hero"
            src="bo.jpg"
          />
        </div>
        <div
          class="lg:flex-grow md:w-1/2 lg:pl-24 md:pl-16 flex flex-col md:items-start md:text-left items-center text-center"
        >
          <h1 class="title-font text-4xl mb-4 font-medium text-gray-900">
            <br class="hidden lg:inline-block" />Welcome to the most beautiful
            library
          </h1>
          <p class="mb-8 leading-relaxed">
            Think about the last good book you read. Did it make you feel more
            connected to others? Maybe it served as a welcome escape. Maybe it
            helped you rediscover the beauty in life. Did it surprise you? As an
            independent bookstore, we strive to offer the same variety and
            richness of experience as the books on our shelves. And because the
            only people we’re beholden to are our customers and ourselves, we
            can focus on what really matters — promoting diverse perspectives,
            upholding the free exchange of ideas, championing the enduring power
            of books, and bolstering the great community of readers and authors
            we’re lucky to be a part of. Thank you for supporting these lofty
            goals. Your choice sustains a family business, and allows us to
            follow our passion for getting the right books into the right hands,
            365 days a year.
          </p>
          <div class="flex justify-center">
            <NuxtLink to="/"
              ><button
                type="button"
                class="m-2 p-4 rounded-xl bg-gradient-to-r from-green-400 to-blue-500 hover:from-pink-500 hover:to-yellow-500 ..."
              >
                Back to Home
              </button>
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>
  </div>
  <section class="text-gray-600 body-font">
    <div class="container px-5 py-24 mx-auto">
      <div class="flex flex-wrap -m-4 text-center">
        <div class="p-4 sm:w-1/4 w-1/2">
          <h2 class="title-font font-medium sm:text-4xl text-3xl text-gray-900">
            2.7K
          </h2>
          <p class="leading-relaxed">Users</p>
        </div>
        <div class="p-4 sm:w-1/4 w-1/2">
          <h2 class="title-font font-medium sm:text-4xl text-3xl text-gray-900">
            1.8K
          </h2>
          <p class="leading-relaxed">Subscribes</p>
        </div>
        <div class="p-4 sm:w-1/4 w-1/2">
          <h2 class="title-font font-medium sm:text-4xl text-3xl text-gray-900">
            35
          </h2>
          <p class="leading-relaxed">Downloads</p>
        </div>
        <div class="p-4 sm:w-1/4 w-1/2">
          <h2 class="title-font font-medium sm:text-4xl text-3xl text-gray-900">
            4
          </h2>
          <p class="leading-relaxed">Products</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style lang="scss" scoped></style>
