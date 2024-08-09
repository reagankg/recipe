<template>    
    <a href="#" class="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700" style="margin: 20px 20px 20px; height: 920px;">

    <h5 class="mb-2 text-lg font-bold tracking-tight text-gray-900 dark:text-white">{{ title }}</h5>
    <h5 class="mb-2 text-base font-bold tracking-tight text-gray-900 dark:text-white">Servings</h5>
    <p class="font-normal text-gray-700 dark:text-gray-400">{{ servings }}</p>
    <h5 class="mb-2 text-base font-bold tracking-tight text-gray-900 dark:text-white">Ingredients</h5>
    <p class="font-normal text-gray-700 dark:text-gray-400">{{ ingredients }}</p>
    <h5 class="mb-2 text-base font-bold tracking-tight text-gray-900 dark:text-white">Instructions</h5>
    <p class="font-normal text-gray-700 dark:text-gray-400">{{ instructions }}</p>
    </a>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props: {
    title: String,
    servings: String,
    ingredients: String,
    instructions: String,
  }
})
</script>