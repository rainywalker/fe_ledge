<template>
    <div id="app">
        <transition name="fade" mode="out-in">
            <router-view/>
        </transition>
    </div>
</template>

<style lang="scss">
    @import '@/assets/reset.scss';
    .fade-enter-active, .fade-leave-active {
        transition: all 0.3s ease;
    }
    .fade-enter, .fade-leave-active {
        opacity: 0;
        transform: scale(1.5);
    }
</style>
