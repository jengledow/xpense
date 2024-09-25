<script setup lang="ts">
    import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
    import { Head, useForm } from '@inertiajs/vue3';
    import Modal from '@/Components/Modal.vue';
    import NumberInput from '@/Components/NumberInput.vue';
    import PrimaryButton from '@/Components/PrimaryButton.vue';
    import { ref } from 'vue';
    import SecondaryButton from '@/Components/SecondaryButton.vue';
    import InputLabel from '@/Components/InputLabel.vue';
    import TextInput from '@/Components/TextInput.vue';

    let total = ref(0);

    const budget = useForm({
        monthly: 100,
        rent: 100,
        utilities: 100
    })

    function validateAndTotal() {
        if(budget.monthly < 0){
            budget.monthly = 0;
        }

        if(budget.rent < 0){
            budget.rent = 0;
        }

        if(budget.utilities < 0){
            budget.utilities = 0;
        }

        total.value = budget.monthly - (budget.rent + budget.utilities);
    }
</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-white leading-tight">Budget</h2>
        </template>

        <div class="flex justify-center">
            <form class="px-2 py-1.5 bg-white border-0 rounded w-11/12 mt-3">
                <div class="my-1">
                    <InputLabel for="monthly" value="Monthly Income:" />
                    <NumberInput 
                        id="monthly"
                        type="number"
                        class="mt-0.5 block w-full"
                        v-model="budget.monthly"
                        autofocus
                        autocomplete="off"
                        @keyup="validateAndTotal"
                        @change="validateAndTotal" 
                    />
                </div>

                <div class="my-1">
                    <InputLabel for="rent" value="Rent:" />
                    <NumberInput 
                        id="rent"
                        type="number"
                        class="mt-0.5 block w-full"
                        v-model="budget.rent"
                        autofocus
                        autocomplete="off"
                        @keyup="validateAndTotal"
                        @change="validateAndTotal"
                    />
                </div>
                <div class="my-1">
                    <InputLabel for="utilities" value="Utilities:" />
                    <NumberInput 
                        id="utilities"
                        type="number"
                        class="mt-0.5 block w-full"
                        v-model="budget.utilities"
                        autofocus
                        autocomplete="off"
                        @keyup="validateAndTotal"
                        @change="validateAndTotal"
                    />
                </div>

                <div class="flex justify-between my-3">
                    <div class="flex items-baseline">
                        <p id="total" class="mx-1 text-2xl" :class="{ 'text-error-red': total <= 0 }">${{ Number(total).toLocaleString('en') }}</p>
                    </div>
                    <SecondaryButton type="submit" :class="{ 'pointer-events-none': total <= 0 }">Update</SecondaryButton> 
                </div>
            </form>
        </div>
    </AuthenticatedLayout>
</template>