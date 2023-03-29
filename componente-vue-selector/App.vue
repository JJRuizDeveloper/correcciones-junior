<template>
  <table class="min-w-full divide-y divide-gray-200 table-auto">
    <thead class="bg-gray-900">
      <tr>
        <th scope="col" class="w-10 text-center">
          <input
            type="checkbox"
            class="w-4 h-4 focus:ring-0"
            @click="checkAll()"
            v-model="checkAllInput"
          />
        </th>
        <th
          scope="col"
          class="w-3/12 text-xs font-semibold tracking-wider text-center text-white uppercase"
        >
          Ciudad
        </th>
        <th
          scope="col"
          class="w-3/12 text-xs font-semibold tracking-wider text-center text-white uppercase"
        >
          Prefix
        </th>
        <th
          scope="col"
          class="w-12 py-3 px-6 text-xs font-semibold tracking-wider text-center text-white uppercase"
        >
          Status
        </th>
      </tr>
    </thead>

    <tbody class="bg-white divide-y divide-gray-200">
      <tr
        v-for="city in cityData"
        :key="city.id"
        class="odd:bg-white even:bg-gray-100"
      >
        <td scope="row" class="text-center px-6 py-4">
          <input
            :id="city.id"
            :value="city.id"
            v-model="city.checked"
            type="checkbox"
            @click="city.checked = !city.checked"
            class="w-4 h-4 focus:ring-0"
          />
        </td>
        <td
          class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white"
        >
          {{ city.name }}
        </td>
        <td class="px-6 py-4 text-center">
          {{ city.slug }}
        </td>
        <td class="px-6 py-4 text-center">
          {{ city.status }}
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import { ref } from "vue";

const checkAll = () => {
 checkAllInput.value = !checkAllInput.value
 cityData.value.forEach((city) => city.checked = checkAllInput.value)
};


const cityData = ref([
  { id: "1", name: "Dato 01", slug: "dato-01", status: "activo", checked: false },
  { id: "2", name: "Dato 02", slug: "dato-02", status: "activo", checked: false },
  { id: "3", name: "Dato 03", slug: "dato-03", status: "activo", checked: false },
  { id: "4", name: "Dato 04", slug: "dato-04", status: "inactivo", checked: false },
  { id: "5", name: "Dato 05", slug: "dato-05", status: "activo", checked: false },
]);

const checkAllInput = ref(false)
</script>