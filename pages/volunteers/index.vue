<template>
  <div>
    <h2>Manage Volunteers</h2>
      <p>This is where you'll see a list of volunteers and links to their profiles!</p>

    <!-- Display search results -->
    <div v-if="searchResult">
      <p>Student response for {{ searchQuery }}</p>
      <p>{{ searchResult }}</p>
    </div>

    <!-- interactive button -->
    <div class="response-button" @click="searchQuery = '1'; search()">
      <div class="info">
        <div class="id-name">
          <p class="id">1</p>
          <p class="name">Shannon Carter</p>
        </div>
        <p class="action">View Volunteer Profile</p>
      </div>
    </div>

    <div class="response-button" @click="searchQuery = '2'; search()">
      <div class="info">
        <div class="id-name">
          <p class="id">2</p>
          <p class="name">Jane Doe</p>
        </div>
        <p class="action">View Volunteer Profile</p>
      </div>
    </div>

  </div>
</template>

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

<style scoped>
h2 {
  margin-bottom: 0px;
  font-size: 36px;
}

h3 {
  margin-bottom: 10px;
  font-size: 15px;
  width: 22%;
  border-bottom: 1px solid rgb(214, 135, 135);
}

.response-button {
  width: 400px;
  height: 100px;
  background-color: #d08e8e;
  border-radius: 10px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
}

.response-button:hover {
  background-color: hsl(209, 34%, 55%);
}

.id-name {
  display: flex;
  justify-content: space-between;
}

.id {
  font-size: 15px;
  margin: 0;
}

.name {
  font-size: 40 px;
  margin: 0;
}

.action {
  font-size: 18px;
  margin: 0;
}

.response-button {
  /* Existing CSS properties */
  margin-top: 10px;
  margin-bottom: 20px;
}
</style> 