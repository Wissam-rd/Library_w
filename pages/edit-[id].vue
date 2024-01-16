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

      <form @submit.prevent="update" class="py-6 px-6">
        <div class="block text-gray-700 font-bold mb-4">ID: {{ post.id }}</div>
        <div class="flex text-gray-700 font-bold mb-2 justify-center">
          NameBook: {{ post.namebook }}
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 font-bold mb-2" for="name">
            Name
          </label>
          <input
            v-model="name"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="Enter your name"
          />
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 font-bold mb-2" for="email">
            Email
          </label>
          <input
            v-model="email"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
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
            placeholder="Enter your phone number"
          />
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 font-bold mb-2"> The price </label>

          <input
            v-model="price"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
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
          ></textarea>
        </div>

        <div class="flex items-center justify-center mb-3">
          <div class="relative inline-flex group">
            <NuxtLink>
              <div
                class="absolute transitiona-all duration-1000 opacity-70 -inset-px bg-gradient-to-r from-[#44BCFF] via-[#FF44EC] to-[#FF675E] rounded-xl blur-lg group-hover:opacity-100 group-hover:-inset-1 group-hover:duration-200 animate-tilt"
              ></div>

              <button
                class="relative inline-flex items-center justify-center px-8 py-3 text-lg font-bold text-white transition-all duration-200 bg-gray-900 font-pj rounded-xl focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-900"
                type="submit"
              >
                Get it now
              </button>
            </NuxtLink>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { createClient } from "@supabase/supabase-js";
const route = useRoute();
const supabase = createClient(
  "https://vwdufkxcsvsywmjjbffm.supabase.co",
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c"
);
const name = ref("");
const email = ref("");
const message = ref("");
const phone = ref("");
const price = ref("");

const update = async () => {
  console.log(name, phone);
  try {
    // Ensure that phone and price are numbers
    const phoneValue = Number(phone.value);
    const priceValue = Number(price.value);

    const { data, error } = await supabase
      .from("reservations")
      .update({
        name: name.value,
        email: email.value,
        phone: isNaN(phoneValue) ? null : phoneValue,
        message: message.value,
        price: isNaN(priceValue) ? null : priceValue,
      })

      .eq("id", route.params.id)
      .select();

    if (error) {
      console.log(error.message);
    }
    console.log(data);
  } catch (error) {
    console.error("Error updating data:", error.message);
    // Handle error condition here
  }
};

const { data: post } = await supabase
  .from("reservations")
  .select()
  .eq("id", route.params.id)
  .maybeSingle();
email.value = post.email;
name.value = post.name;
price.value = post.price;
phone.value = post.phone;
message.value = post.message;
</script>
