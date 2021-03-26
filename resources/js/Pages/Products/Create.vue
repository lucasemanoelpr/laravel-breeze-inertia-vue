<template>
    <breeze-authenticated-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Create new product
            </h2>
        </template>

        <div class="flex items-center bg-gray-50 dark:bg-gray-900 py-2">
            <div class="container mx-auto">
                <div class="max-w-md mx-auto bg-white p-5 rounded-md shadow-sm">                    
                    <form @submit.prevent="form.post('/products')">
                        <div class="mb-6">
                            <label for="name" class="block mb-2 text-sm text-gray-600 dark:text-gray-400">Product Name</label>
                            <input type="text" v-model="form.name" class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500" />
                            <div v-if="form.errors.name">{{ form.errors.name }}</div>
                        </div>

                        <div class="mb-6">
                            <label for="price" class="block mb-2 text-sm text-gray-600 dark:text-gray-400">Price</label>
                            <input type="text" v-model="form.price" class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500" />
                            <div v-if="form.errors.name">{{ form.errors.price }}</div>
                        </div>

                        <div class="mb-6">                            
                            <input type="checkbox" v-model="form.active" />
                            <label class="pl-1 pt-1">Active? </label>
                            <div v-if="form.errors.name">{{ form.errors.active }}</div>
                        </div>

                        <div class="mb-6 flex justify-end">
                            <button type="submit" :disabled="form.processing" class=" w-24 px-3 py-4 text-white bg-indigo-500 rounded-md focus:bg-indigo-600 focus:outline-none">Save</button>
                        </div>                
                    </form>                  
                </div>
            </div>
        </div>

    </breeze-authenticated-layout>
</template>

<script>
    import BreezeAuthenticatedLayout from '@/Layouts/Authenticated'

    export default {
        components: {
            BreezeAuthenticatedLayout,
        },
        data() {
            return {
            form: this.$inertia.form({
                name: null,
                price: null,
                active: true,
            }),
            }
        },
    }
</script>
