<template>
<div class="absolute  w-full top-0 ">
    <header class="text-white z-30 body-font">
    <span class="m-2 mt-2 w-20px h-20px text-yellow-60 text-opacity-50 text-base font-mono shadow-lg shadow-cyan-500/50">Online Book Store</span> 
    <div class="container mx-auto flex flex-wrap  p-2 flex-col md:flex-row items-center">
    <a class="flex title-font font-medium items-center justify-center text-white mb-2 md:mb-0">
    <img src="online-library.png" class="w-10" alt=""> 
   <span class="   ml-3 text-2xl text-white">Bookes IT</span>
   </a>
  <nav class="m-auto flex gap-2  text-lg items-center  justify-center  cursor-pointer">
   <NuxtLink to="/"><a class="mr-5  hover:text-red-800 ">Home</a></NuxtLink> 
   <NuxtLink to="about"><a class="mr-5 hover:text-red-800">About</a></NuxtLink> 
   <NuxtLink to="Store"><a class="mr-5  hover:text-red-800">Stores</a></NuxtLink> 
  </nav>
 <NuxtLink to="login"><button class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700">
<span class="relative px-4 py-2.5 transition-all ease-in duration-75  dark:bg-gray-900 rounded-md group-hover:bg-opacity-0">
Login
</span>
</button></NuxtLink> 
</div>
  </header>
  </div>
  <main class="m-0">
    <div class="intro">
      <h1 class="font-sans text-7xl text-white font-bold m-0 uppercase">
        The best book store
      </h1>
      <p class="text-xl text-white uppercase m-5">
        I am a web developer and I love to create websites.
      </p>
    
      <NuxtLink to="/topBook"
        ><button class=" animate-pulse relative inline-flex items-center justify-center p-0.5 mb-10 me-2 overflow-hidden text-sm font-bold text-gray-900 rounded-lg group bg-gradient-to-br from-purple-500 to-pink-500 group-hover:from-purple-500 group-hover:to-pink-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-purple-200 dark:focus:ring-purple-800">
<span class="relative px-12 py-2.5 transition-all ease-in duration-75 bg-white  dark:bg-gray-900 rounded-md group-hover:bg-opacity-0 ">
Welcome
</span>
</button>
      </NuxtLink>
    </div>
  </main>
</template>
<style>
.intro {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height:707px;
  background: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.5) 0%,
      rgba(0, 0, 0, 0.5) 100%
    ),
    url(home.jpg);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
</style>
