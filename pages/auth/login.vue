<script setup lang="ts">
const supabase = useSupabaseClient();
const email = ref("");

const signInWithOtp = async () => {
  const { error } = await supabase.auth.signInWithOtp({
    email: email.value,
    options: {
      emailRedirectTo: "http://localhost:3000/auth/confirm"
    }
  });
  if (error) console.log(error);
};

const signInWithOAuth = async () => {
  const { error } = await supabase.auth.signInWithOAuth({
    provider: "github",
    options: {
      redirectTo: "http://localhost:3000/auth/confirm"
    }
  });
  if (error) console.log(error);
};
</script>
<template>
  <div>
    <!-- component -->
    <div class="flex h-screen">
      <!-- Right Pane -->
      <div class="w-full flex items-center justify-center">
        <div class="max-w-md w-full p-6">
          <h1 class="text-3xl font-semibold mb-6 text-white text-center">
            Sign Up
          </h1>
          <h1 class="text-sm font-semibold mb-6 text-gray-300 text-center">
            Join to Our Community with all time access and free
          </h1>
          <div
            class="mt-4 flex flex-col lg:flex-row items-center justify-between"
          >
            <div class="w-full lg:w-1/2 mb-2 lg:mb-0">
              <button
                type="button"
                class="w-full flex justify-center items-center gap-2 bg-white text-sm text-gray-600 p-2 rounded-md hover:bg-gray-50 border border-gray-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-200 transition-colors duration-300"
              >
                <img src="~/assets/img/google.svg" class="w-4" alt="">
                Sign Up with Google
              </button>
            </div>
            <div class="w-full lg:w-1/2 ml-0 lg:ml-2">
              <button
                type="button"
                class="w-full flex justify-center items-center gap-2 bg-white text-sm text-gray-600 p-2 rounded-md hover:bg-gray-50 border border-gray-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-200 transition-colors duration-300"
                @click="signInWithOAuth()"
              >
                <img src="~/assets/img/github.svg" class="w-4" alt="">
                Sign Up with Github
              </button>
            </div>
          </div>
          <div class="mt-4 text-sm text-gray-600 text-center">
            <p>or with email</p>
          </div>
          <form action="#" method="POST" class="space-y-4">
            <!-- Your form elements go here -->
            <div>
              <label for="email" class="block text-sm font-medium text-gray-300"
                >Email</label
              >
              <input
                type="text"
                id="email"
                name="email"
                class="mt-1 p-2 w-full border rounded-md focus:border-gray-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-300 transition-colors duration-300"
              />
            </div>
            <div>
              <label
                for="password"
                class="block text-sm font-medium text-gray-300"
                >Password</label
              >
              <input
                type="password"
                id="password"
                name="password"
                class="mt-1 p-2 w-full border rounded-md focus:border-gray-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-300 transition-colors duration-300"
              />
            </div>
            <div>
              <button
                type="submit"
                class="w-full bg-black text-white p-2 rounded-md hover:bg-gray-800 focus:outline-none focus:bg-black focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-900 transition-colors duration-300"
              >
                Sign In
              </button>
            </div>
          </form>
          <div class="mt-4 text-sm text-gray-600 text-center">
            <p>
              You don't have any account, right?
              <NuxtLink to="/auth/register" class="text-white hover:underline">Register here</NuxtLink>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
