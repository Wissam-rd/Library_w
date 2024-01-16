<template>
  <div>
<aside class=" text-3xl flex flex-col w-50 h-screen px-5 py-8 overflow-y-auto bg-black border-r rtl:border-r-0 rtl:border-l dark:bg-red-600 dark:border-gray-700">
  <NuxtLink to="topBook" class="flex items-center px-3 py-4 text-yellow-50 transition-colors duration-300 transform rounded-lg dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-800 dark:hover:text-gray-200 hover:text-gray-700" href="#">
      <Icon name="fxemoji:books" color="black" />
     <div> <span class="mx-2 text-sm font-medium">TopBook</span></div>  
    </NuxtLink>
    <NuxtLink to="philosophical" class="flex items-center px-3 py-4 text-yellow-50 transition-colors duration-300 transform rounded-lg dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-800 dark:hover:text-gray-200 hover:text-gray-700" href="#">
      <Icon name="fxemoji:books" color="black" />
     <div> <span class="mx-2 text-sm font-medium">Philosophical</span></div>  
    </NuxtLink>
    
    <NuxtLink to="historicity">
      <a class="flex items-center px-3 py-4 text-yellow-50 transition-colors duration-300 transform rounded-lg dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-800 dark:hover:text-gray-200 hover:text-gray-700" href="#">
      <Icon name="fxemoji:books" color="black" /> <span class="mx-2 text-sm font-medium">historicity</span>   
    </a></NuxtLink>
   
       <NuxtLink to="Islamic"> <a class="flex items-center px-3 py-4 text-yellow-50 transition-colors duration-300 transform rounded-lg dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-800 dark:hover:text-gray-200 hover:text-gray-700" href="#">
      <Icon name="fxemoji:books" color="black" /><span class="mx-2 text-sm font-medium">Islamic</span>
    </a></NuxtLink>
    
        <NuxtLink to="novels"><a class="flex items-center px-3 py-4 text-yellow-50 transition-colors duration-300 transform rounded-lg dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-800 dark:hover:text-gray-200 hover:text-gray-700" href="#">
      <Icon name="fxemoji:books" color="black" /><span class="mx-2 text-sm font-medium">Novels</span>
    </a></NuxtLink>
    

  
   
</aside>


</div>

</template>