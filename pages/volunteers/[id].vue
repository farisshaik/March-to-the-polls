<template>
    <div>
        <p>Volunteer Profile for {{ id }}</p>
        <p>This is where you'll see their response!</p>
    </div>
</template>

<script setup>
    const { id } = useRoute().params

    definePageMeta({
        layout: 'volunteers'
    })
</script>

<style scoped>

</style>

