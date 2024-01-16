<template><div class=" w-full top-0  ">
    <header class="text-white z-30 bg-black body-font ">
      
    <span class=" ml-4 mt-4 w-20px h-20px text-yellow-60 text-opacity-50 text-base font-mono shadow-lg shadow-cyan-500/50">Online Book Store</span> 
    <div class="container mx-auto flex flex-wrap  p-2 flex-col md:flex-row items-center">
    <a class="flex title-font font-medium items-center justify-center text-white mb-2 md:mb-0">
    <img src="online-library.png " class="w-10 ml-3" alt=""> 
   <span class="  p ml-3 text-2xl text-white">Bookes IT</span>
   </a>
  <nav class="m-auto flex gap-2  text-lg items-center  justify-center  cursor-pointer">
   <NuxtLink to="/"><a class="mr-5  hover:text-red-800 ">Home</a></NuxtLink> 
   <NuxtLink to="about"><a class="mr-5 hover:text-red-800">About</a></NuxtLink> 
   <NuxtLink to="Store"><a class="mr-5  hover:text-red-800">Store</a></NuxtLink> 
  </nav>
 <NuxtLink to="login"><button class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700">
<span class="relative px-4 py-2.5 transition-all ease-in duration-75  dark:bg-gray-900 rounded-md group-hover:bg-opacity-0">
Login
</span>
</button></NuxtLink> 

</div>

  </header>
  </div> </template>
