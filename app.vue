<template>
  <form class="text-gray-600 body-font">
    <div class="container px-5 py-24">
      <div class="lg:w-3/5 md:w-1/2">
        <h1 class="text-gray-900">Subscribe to my newsletter</h1>
        <p class="leading-relaxed mt-4">
          I send out a weekly newsletter with tips and tricks for web
          development.
        </p>
      </div>
      <div class="lg:w-2/6 md:w-1/2 bg-gray-100 px-3 py-3 rounded-md">
        <h2 class="text-gray-900 text-lg font-medium title-font mb-5">
          Subscribe
        </h2>

        <div class="relative mb-4">
          <label for="email" class="leading-7 text-sm text-gray-600"
            >Email</label
          >
          <input
            type="email"
            id="email"
            name="email"
            class="w-full bg-white rounded py-4 ring-1"
          />
        </div>
        <button class="text-white bg-indigo-500 px-2 rounded py-3">
          Subscribe
        </button>
      </div>
    </div>
  </form>
</template>

<script lang="ts" setup>
import './assets/css/tailwind.css';

// variable to hold the response from supabase
const DBResponse = ref([]);
// variable to hold the provided email address
const userEmail = ref('');
// function to send email to our server route
async function postToDB() {
  const result = await fetch(`/api/subscribe?email=${userEmail.value}`);
  const data = await result.json();
  DBResponse.value = data;
}
</script>
