<template>
  <div>
    <h2>Access Student Responses</h2>
    <h3>View and edit past Student Responses</h3>
    <p>This is where you can access the Student Response Form Database as well as filter and sort responses using an ID number in the search bar.</p>

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
          <p class="name">Tawba Wohid</p>
        </div>
        <p class="action">View Student Response</p>
      </div>
    </div>

    <div class="response-button" @click="searchQuery = '2'; search()">
      <div class="info">
        <div class="id-name">
          <p class="id">2</p>
          <p class="name">John Doe</p>
        </div>
        <p class="action">View Student Response</p>
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
    router.push(`/students/${searchQuery.value}`)
  }

  definePageMeta({
    layout: 'students'
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