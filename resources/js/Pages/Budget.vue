<script setup lang="ts">
    import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
    import { Head } from '@inertiajs/vue3';
    import SecondaryButton from '@/Components/SecondaryButton.vue';
</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-white leading-tight">Budget</h2>
        </template>

        <div>
            <SecondaryButton>
                Set Budget
            </SecondaryButton>
        </div>
    </AuthenticatedLayout>
</template>