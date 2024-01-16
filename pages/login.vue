<template>
  <div>
    <section class="min-h-screen py-7 bg-gray-200">
      <div class="container mx-auto h-full">
        <div class="flex justify-center items-center h-full">
          <div class="w-full lg:w-11/12">
            <div class="bg-white rounded-lg shadow-lg">
              <div class="p-8 md:p-20">
                <div class="flex justify-center">
                  <div class="w-full md:w-10/12 lg:w-5/12">
                    <p class="text-center text-4xl font-bold mb-8">Register</p>

                    <form class="px-4 md:px-8"></form>

                    <div class="flex items-center mb-6">
                      <div class="flex-1">
                        <label>Email</label>
                        <input
                          type="email"
                          class="border-b-2 border-gray-400 focus:outline-none w-full py-2"
                          v-model="email"
                        />
                      </div>
                    </div>
                    <div class="flex items-center mb-6">
                      <div class="flex-1">
                        <label>Password</label>
                        <input
                          type="password"
                          class="border-b-2 border-gray-400 focus:outline-none w-full py-2"
                          v-model="password"
                        />
                      </div>
                    </div>
                  
                      <p id="filled_success_help" class="mt-2 text-xs text-red-800 dark:text-green-400"><span class="font-medium">{{ errorMsg }}</span> </p>

                    
                    <div class="flex justify-center">
                      <button
                        @click="login"
                        class="bg-blue-500 text-white font-bold py-3 px-8 rounded-lg"
                      >
                        <span> log in</span>
                      </button>
                    </div>
                    
                    <button
                      class="w-full mt-8 text-sm text-center underline text-slate-300"
                    ></button>

                  </div>
                  <div class="md:block md:w-7/12 lg:w-7/12 flex items-center">
                    <img
                      src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-registration/draw1.webp"
                      class="w-full"
                      alt="Sample image"
                    />
                    
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRoute } from "vue-router";
import { createClient } from "@supabase/supabase-js";
const supabase = createClient(
  "https://vwdufkxcsvsywmjjbffm.supabase.co",
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ3ZHVma3hjc3ZzeXdtampiZmZtIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAzODk3ODIsImV4cCI6MjAxNTk2NTc4Mn0.SnraTVQnGrZvPDKhtuwmdgaPZvshlSFEvDreUFnRp9c"
);

const router = useRoute();
const email = ref('');
const password = ref('');
const errorMsg = ref(null);

async function login() {
  try {
    let { data, error } = await supabase.auth.signInWithPassword({
      email: email.value,
      password: password.value,
    });
      console.log(data.user);
    if (data.user) {
      
      navigateTo("reservations");
    } else {
      // Redirect or perform actions after successful login
     errorMsg.value= error.message
    }
  } catch (error) {
    errorMsg.value = error.message;
  }
}

</script>
