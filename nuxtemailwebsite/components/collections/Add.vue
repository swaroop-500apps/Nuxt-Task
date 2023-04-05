<template>
    <div v-if="open">
        <div @close="open = false">
            <label for="companyname" class="block text-sm font-medium leading-6 text-gray-900">Add Company</label>
            <div class="mt-2">
                <input type="companyname" name="companyname" id="companyname"
                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                    placeholder="Enter a Company name" v-model="company_name"/>
            </div>
            <div class="mt-2">
                <input type="companyurl" name="companyurl" id="companyurl"
                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                    placeholder="Enter a Company url" v-model="company_url" />
            </div>
            <div class="mt-6 flex items-center justify-end gap-x-6">
                <button type="submit"
                    class="rounded-md bg-indigo-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                    @click.prevent="cancelmethod()">Cancel</button>
                <button type="submit"
                    class="rounded-md bg-indigo-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                    @click.prevent="savemethod()">Save</button>
            </div>
        </div>
    </div>
</template>
<script setup>
import { ref, onMounted } from 'vue'
const { $bus } = useNuxtApp()

const props = defineProps({ open: Boolean })
let company_url =ref('')
let company_name =ref('')
const Addcompanydetails = () => {
    open.value = true
}
const form= ref('')
const savemethod = async () => {

    let options = {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
        Authorization:
          "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiM2FiNGRhMmU2ZmZlNDFhMThkMjBhY2U5NDM1MjI5MmYiLCJkIjoiMTY4MDA5MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODMxOTN9.Syb1XQeqr9lBLaIeS2TCyl760cmliwBooz9oRcrGCjo",
      },
      body: JSON.stringify(form.value),
    };
    const { data: addCompanyData } = await useAuthLazyFetchPost(
      "https://v1-orm-lib.mars.hipso.cc/websites/",
      options
    );
    companyData.value.unshift(form.value);
    form.value = {};
  };
</script>
