<template>
    <div>
        <header class="shadow-sm bg-white">
            <nav class="container mx-auto p-4 flex justify-between">
                <NuxtLink to="/" class="font-bold">March to the Polls</NuxtLink>
                <ul class="flex gap-4">
                    <li><NuxtLink to="/" style="display:contents">Home</NuxtLink></li>
                    <li><NuxtLink to="/about" style="display:contents">About</NuxtLink></li>
                    <li><NuxtLink to="/volunteers" style="display:contents">Volunteers Logs</NuxtLink></li>
                    <li><NuxtLink to="/logVisit" style="display:contents">Log a Visit</NuxtLink></li>
                    <li><NuxtLink to="/studentForm" style="display:contents">Sudents Form</NuxtLink></li>
                    <li><NuxtLink to="/students" class="btn">Students</NuxtLink></li>
                </ul>
            </nav>
        </header>

        <!-- output the page content--> 
        <div class="container mx-auto p-4"> 
            <slot />
        </div>
    </div>
 </template>

 <style scoped>
    .router-link-exact-active {
        color:#2b11ae;
    }
</style>