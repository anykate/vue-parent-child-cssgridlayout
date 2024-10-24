<script setup>
import { ref } from 'vue'

const toggleExpand = ref(false)

const handleClick = () => {
    toggleExpand.value = !toggleExpand.value
}
</script>

<template>
    <div
        class="wrapper"
        :class="{ 'sb-expand': toggleExpand }"
    >
        <header class="dashboard-header">
            <router-link :to="{ name: 'Home' }">Home</router-link> |
            <router-link :to="{ name: 'About' }">About</router-link>
        </header>
        <aside class="dashboard-sidebar">
            <div class="logo">&#9812;</div>
            <button
                type="button"
                @click="handleClick"
            >
                &#9776;
            </button>
        </aside>
        <main class="dashboard-main">
            <router-view />
        </main>
        <footer class="dashboard-footer">Footer</footer>
    </div>
</template>

<style scoped>
.wrapper {
    display: grid;

    min-block-size: 100vh;
    min-block-size: 100dvh;

    grid-template-columns: 5rem 1fr;
    grid-template-rows: auto 1fr auto;

    /* grid-template-areas:
        'header header'
        'sidebar main'
        'footer footer'; */

    grid-template-areas:
        'sidebar header'
        'sidebar main'
        'sidebar footer';

    transition: grid-template-columns 0.3s ease;

    &.sb-expand {
        grid-template-columns: 12.5rem 1fr;
    }
}

.dashboard-header {
    grid-area: header;
    background-color: #fff;
    padding: 1.25rem;
}

.dashboard-footer {
    grid-area: footer;
    background-color: #fff;
    padding: 1.25rem;
}

.dashboard-main {
    grid-area: main;
    padding: 1.25rem;
}

.dashboard-sidebar {
    position: relative;
    grid-area: sidebar;
    background-color: #1d1d29;
    color: #fff;
}

.dashboard-sidebar button {
    position: absolute;
    inset: 4.5rem -0.75rem auto auto;
    width: 1.5rem;
    aspect-ratio: 1;
    background-color: #fff;
    border: transparent;
    border-radius: 50%;
    cursor: pointer;
}

.logo {
    display: flex;
    justify-content: center;
    font-size: 3rem;
    line-height: 1.3;
}
</style>
