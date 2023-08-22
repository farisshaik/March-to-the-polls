<template>
    <div>
        <p>Student response for {{ id }}</p>
        <p>This is where you'll see their response!</p>
    </div>
</template>

<script setup>
    const { id } = useRoute().params

    definePageMeta({
        layout: 'students'
    })
</script>

<style scoped>

</style>

