<template>
    <div class="md:flex md:items-center md:justify-between">
        <div class="min-w-0 flex-1">
            <h2 class="text-2xl font-bold leading-7 text-white sm:truncate sm:text-3xl sm:tracking-tight">Company Details
            </h2>
            <div>
                <h1> <button type="button"
                        class="inline-flex items-center rounded-md bg-white/10 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-white/20"
                        @click="Addcompanydetails()">Add Company</button></h1>
                <tbody class="divide-y divide-gray-200">
                    <tr>
                        <div>
                            <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0">
                                Company Name         
                            </td>
                            <td class="whitespace-nowrap py-4 px-3 text-sm text-gray-500">
                                Company url
                            </td>
                            <button type="button"
                                class="inline-flex items-center rounded-md bg-white/10 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-white/20"
                                @click="Editcompanydetails()">Edit</button>
                            <button type="button"
                                class="ml-3 inline-flex items-center rounded-md bg-indigo-500 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-500">Delete</button>
                        </div>
                    </tr>
                </tbody>
            </div>
        </div>
        <CollectionsAdd v-if="open" :open="open" />
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const { $bus } = useNuxtApp()
const open = ref(false)
const Addcompanydetails = () => {
    open.value = true
}
const Editcompanydetails = () => {
    console.log("open Editcompanydetailsid")
    $bus.$emit('Editcompanydetailsid')
}
</script>

