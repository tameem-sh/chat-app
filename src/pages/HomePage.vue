<template>
    <section>
        <div class="container chat-view">
            <Contact />
            <Chat />
        </div>
    </section>
</template>

<script setup>
import Contact from "@/components/ContactsComponent.vue"
import Chat from "@/components/ChatComponent.vue"
</script>

<style lang="scss" scoped>
section {
    padding-block: 5rem;
    background: $main-bg;
    color: $main-color;
    height: 100vh;
    
    .chat-view {
        height: 100%;
        display: flex;
        gap: 2rem;
    
        & > * {
            background: $section-bg;
            border-radius: 14px;
            padding: 2rem 1rem;
        }
    }
}
</style>