<template>
    <div style="padding: 50px">
        <h1>Data Fetching</h1>
        <hr>
        <div v-for="post in posts" :key="post.id">
            <h2>{{ post.id }} - {{ post.title }}</h2>
            <p>{{ post.body }}</p>
        </div>
        <h2 v-if="pending">Loading....</h2>
        <button @click="prev">prev</button>
        <button @click="next">next</button>
    </div>
</template>

<script setup>
const start = ref(0);

// const { data: posts, error, refresh, pending } = await useFetch('https://jsonplaceholder.typicode.com/posts')
// const { data: posts, error, refresh, pending } = await useFetch(() => `https://jsonplaceholder.typicode.com/posts?_start=${start.value}&_limit=5`)
// console.log(posts.value, error.value?.message);

const { data: posts, error, refresh, pending } = useLazyFetch(() => `https://jsonplaceholder.typicode.com/posts?_start=${start.value}&_limit=5`)

function next() {
    start.value += 5;
    refresh()
}

function prev() {
    start.value -= 5;
    refresh()
}

</script>