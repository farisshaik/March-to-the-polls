<template>
    <div>
      <header class="shadow-sm bg-white flex items-center justify-between">
        <div class="container mx-auto p-4">
          <NuxtLink to="/volunteers" class="font-bold">March to the Polls Manage Volunteers</NuxtLink>
        </div>
        <!-- Search Form -->
        <form @submit.prevent="search" class="mr-4">
          <label>
            Search by ID:
            <input type="text" v-model.trim="searchQuery" required />
          </label>
          <button type="submit">Search</button>
        </form>
      </header>
  
      <!-- output the page content-->
      <div class="container mx-auto p-4">
        <slot />
      </div>
  
      <footer class="container mx-auto p-4 flex justify-between border-t-2">
        <ul class="flex gap-4">
          <li><NuxtLink to="/about" style="display:contents">About</NuxtLink></li>
          <li><NuxtLink to="/volunteers" style="display:contents">Volunteer Logs</NuxtLink></li>
          <li><NuxtLink to="/logVisit" style="display:contents">Log a Visit</NuxtLink></li>
          <li><NuxtLink to="/studentForm" style="display:contents">Sudents Form</NuxtLink></li>
          <li><NuxtLink to="/students" style="display:contents">Students</NuxtLink></li>
        </ul>
      </footer>
    </div>
  </template>
  
  <style scoped>
    .router-link-exact-active {
      color: #831a11;
    }
    
    /* Add this CSS rule */
    header {
      display: flex;
      flex-direction: row;
      align-items: center;
    }
  </style>
  
  <script setup>
    import { ref } from 'vue'
    import { useRouter } from 'vue-router'
  
    const searchQuery = ref('')
    const searchResult = ref(null)
  
    const router = useRouter()
  
    async function search() {
      // Call an API endpoint or fetch data from a database to get the response for the specified ID
      const response = await fetch(`/api/responses/${searchQuery.value}`)
      const data = await response.json()
      // Update the searchResult variable with the retrieved data
      searchResult.value = data.response
      // Navigate to the [id] route to display the search results
      router.push(`/volunteers/${searchQuery.value}`)
    }
  
    
    definePageMeta({
      layout: 'volunteers'
    })
  </script>
  