<template>
  <div>
    <div
      class="max-w-md mx-auto mt-1 bg-white shadow-lg rounded-lg overflow-hidden"
    >
      <div
        class="text-2xl py-4 px-6 bg-gray-900 text-white text-center font-bold uppercase"
      >
        Welcome
      </div>
      <form @submit.prevent="insert" class="py-4 px-6">
        <div class="mb-4">
          <div class="flex text-gray-700 font-bold m-5 justify-center">
            BookName ({{ post.title }})
          </div>
          <div class="flex text-gray-700 font-bold m-5">
            The price:{{ post.price }}
          </div>
          <label class="block text-gray-700 font-bold mb-2" for="name">
            Name
          </label>
          <input
            v-model="name"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="Enter your name"
            required
          />
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 font-bold mb-2" for="email">
            Email
          </label>
          <input
            v-model="email"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            id="email"
            type="email"
            placeholder="Enter your email"
          />
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 font-bold mb-2">
            Phone Number
          </label>
          <input
            v-model="phone"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            id="phone"
            type="tel"
            placeholder="Enter your phone number"
            required
          />
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 font-bold mb-2" for="message">
            Message
          </label>
          <textarea
            v-model="message"
            class="shadow appearance-none border rounded w-full py-0 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            id="message"
            rows="4"
            placeholder="Enter any additional information"
            required
          ></textarea>
        </div>

        <div class="flex items-center justify-center mb-3">
          <div class="relative inline-flex group">
            <div
              class="absolute transitiona-all duration-1000 opacity-70 -inset-px bg-gradient-to-r from-[#44BCFF] via-[#FF44EC] to-[#FF675E] rounded-xl blur-lg group-hover:opacity-100 group-hover:-inset-1 group-hover:duration-200 animate-tilt"
            ></div>
            <Nuxt-link to="thank">
              <button
                class="animate-bounce relative inline-flex items-center justify-center px-8 py-3 text-lg font-bold text-white transition-all duration-200 bg-gray-900 font-pj rounded-xl focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-900"
                type="submit"
              >
                Get it now
              </button>
            </Nuxt-link>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { createClient } from "@supabase/supabase-js";
const supabase = createClient(
  "https://vwdufkxcsvsywmjjbffm.supabase.co",
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c"
);
const headers = {
  apikey:
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c",
};

const route = useRoute();

const { data: post } = await supabase
  .from("books")
  .select()
  .eq("id", route.params.id)
  .maybeSingle();

console.log(post);
const name = ref("");
const email = ref("");
const message = ref("");
const phone = ref("");

const insert = async () => {
  try {
    const { data, error } = await supabase.from("reservations").insert([
      {
        name: name.value,
        email: email.value,
        phone: Number(phone.value),
        message: message.value,
        namebook: post.title,
        price: post.price,
      },
      // Add other fields as needed
    ]);

    if (error) {
      throw new Error("Failed to insert data");
    } else {
      console.log("Data inserted:", data);
      // Optionally, handle successful insertion here
    }
  } catch (error) {
    console.error("Error inserting data:", error.message);
    // Handle error condition here
  }
};
</script>
