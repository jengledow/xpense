<script setup lang="ts">
withDefaults(
    defineProps<{
        type?: 'button' | 'submit' | 'reset';
    }>(),
    {
        type: 'button',
    }
);
</script>

<template>
    <button
        :type="type"
        class="inline-flex items-center px-4 py-2 bg-orange border border-gray-300 rounded-md font-semibold text-xs text-dark-green uppercase tracking-widest shadow-sm hover:bg-dark-green hover:text-white focus:outline-none focus:ring-2 focus:ring-light-green focus:ring-offset-2 disabled:opacity-25 transition ease-in-out duration-150"
    >
        <slot />
    </button>
</template>
