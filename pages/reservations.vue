<template>
  <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
    <div
      class="flex items-center justify-between flex-column flex-wrap md:flex-row space-y-4 md:space-y-0 pb-4 bg-white dark:bg-gray-900"
    >
      <button
        type="button"
        class="text-white uppercase bg-gradient-to-r m-6 from-cyan-400 via-cyan-500 to-cyan-600 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-cyan-300 dark:focus:ring-cyan-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2"
      >
        page reservations
      </button>
      <button
        @click="snout"
        class="focus:outline-none text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900"
      >
        Singe out
      </button>
      <label for="table-search" class="sr-only">Search</label>

      <div class="relative">
        <div
          class="absolute inset-y-0 rtl:inset-r-0 start-0 flex items-center ps-3 pointer-events-none"
        >
          <svg
            class="w-9 h-4 text-gray-500 dark:text-gray-400"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 20 20"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"
            />
          </svg>
        </div>
        <input
          @input="searchUser"
          v-model="searchTerm"
          type="text"
          id="table-search-users"
          class="block p-2 ps-10 text-sm text-gray-900 border border-gray-300 rounded-lg w-80 bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Search for users"
        />
      </div>
    </div>

    <table
      class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400"
    >
      <thead
        class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400"
      >
        <tr>
          <th scope="col" class="p-4 gap-5">
            <div class="flex items-center">
              <div>ID</div>
            </div>
          </th>
          <th scope="col" class="px-8 py-3">Name</th>
          <th scope="col" class="px-8 py-3">Date</th>
          <th scope="col" class="px-6 py-3">Book Name</th>
          <th scope="col" class="px-6 py-3">phone</th>
          <th scope="col" class="px-6 py-3">the price</th>
          <th scope="col" class="px-6 py-3">message</th>
          <th scope="col" class="px-16 py-3">Action</th>
        </tr>
      </thead>
      <!--   filteredInfos -->
      <tbody v-for="info in infos" :key="info.id">
        <tr
          class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600"
        >
          <td class="w-4 p-4">
            <div class="flex items-center justify-center">
              <div class="text-black font-serif">{{ info.id }}</div>
            </div>
          </td>
          <th
            scope="row"
            class="flex items-center px-6 py-4 text-gray-900 whitespace-nowrap dark:text-white"
          >
            <div class="ps-3">
              <div class="text-base text-black font-semibold">
                {{ info.name }}
              </div>
              <div class="font-normal text-gray-500">
                {{ info.email }}
              </div>
            </div>
          </th>
          <td class="px-6 py-4 text-black font-semibold">
            {{ info.created_at }}
          </td>
          <td class="px-6 py-4 text-black font-semibold">
            {{ info.namebook }}
          </td>
          <td class="px-6 py-4 text-black font-semibold">{{ info.phone }}</td>
          <td class="px-4 py-4">
            <div class="flex items-center text-black font-semibold">
              <div class="h-2.5 w-2.5 rounded-full me-2"></div>
              $ {{ info.price }}
            </div>
          </td>

          <td class="px-4 py-4">
            <div
              class="flex items-center line-clamp-3 tracking-widest text-black font-semibold"
            >
              <div class="h-2.5 w-2.5 rounded-full me-2"></div>
              {{ info.message }}
            </div>
          </td>

          <td class="flex gap-4 px-6 py-4">
            <NuxtLink :to="`edit-${info.id}`">
              <button
                class="text-white bg-blue-700 hover:bg-blue-800 focus:outline-none focus:ring-4 focus:ring-blue-300 font-medium rounded-full text-sm px-5 py-2.5 text-center me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
              >
                <Icon name="fa6-solid:user-pen"></Icon></button
            ></NuxtLink>

            <button
              @click="deleteuser(info.id)"
              class="text-white bg-red-700 hover:bg-red-800 focus:outline-none focus:ring-4 focus:ring-red-300 font-medium rounded-full text-sm px-5 py-2.5 text-center me-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900"
            >
              <Icon name="fa6-solid:trash-can"></Icon>
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import { createClient } from "@supabase/supabase-js";

const supabase = createClient(
  "https://vwdufkxcsvsywmjjbffm.supabase.co",
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c"
);
const headers = {
  apikey:
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c",
};

const { pending, data: infos } = await useFetch(
  "https://vwdufkxcsvsywmjjbffm.supabase.co/rest/v1/reservations?select=*",
  { headers: headers }
);
const filteredInfos = ref([]);
const searchTerm = ref("");
const router = useRouter();

const searchUser = async () => {
  try {
    const { data: info, error } = await supabase
      .from("reservations")
      .select("*")
      .eq("name", searchTerm.value);
    if (error) {
      console.error("Error fetching user:", error.message);
      return;
    }

    infos.value = info;

    // Do something with the fetched data (users)
  } catch (error) {
    console.error("Exception:", error);
  }
};

const deleteuser = async (id) => {
  try {
    const { error } = await supabase.from("reservations").delete().eq("id", id);

    if (error) {
      console.error("Error deleting user:", error.message);
      return;
    }

    window.location.reload(); // Reload the page after deletion
  } catch (error) {
    console.error("Exception:", error);
  }
};

const snout = async () => {
  try {
    const { error } = await supabase.auth.signOut();
    if (error) {
      console.error("Error signing out:", error.message);
    } else {
      console.log("Sign-out successful!");
      router.push("/login"); // Redirect to the login page
    }
  } catch (error) {
    console.error("Exception:", error);
  }
};
</script>
