<script setup>
import { useOnline } from '@vueuse/core'

const online = useOnline();
let show_alert = ref(false);

if (online.value) {
    show_alert.value = true
}


watch(online, (newValue, oldValue) => {
    if (newValue) {
        show_alert.value = true
    } else {
        show_alert.value = false
    }
});

</script>

<template>
    <section v-show="show_alert" class="w-full h-[60px]  flex justify-end items-center mx-auto box-border p-5">
        <div class="container flex justify-end items-center">
            <span class="font-bold text-lg mr-2">.اتصال به اینترنت شما بدون مشکل می باشد</span>
            <span class="relative flex h-3 w-3">
                <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"></span>
                <span class="relative inline-flex rounded-full h-3 w-3 bg-green-500"></span>
            </span>
        </div>
    </section>
</template>

<style scoped></style>