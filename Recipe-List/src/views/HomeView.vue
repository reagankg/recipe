<template>
  <SignIn v-if="!userId" after-sign-in-url="/" sign-up-url="/sign-up" />
  <div
    v-else
    style="display: flex; flex-direction: row; flex-wrap: wrap; justify-content: space-evenly;" 
  >
    <div v-for="(item, index) in recipeData" :key="index"> 
      <Card :title="item.title" :ingredients="item.ingredients" :servings="item.servings" :instructions="item.instructions" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { SignIn } from 'vue-clerk';
import { useAuth } from 'vue-clerk';
import Card from '../components/card.vue';

// Reactive reference for recipe data
const recipeData = ref<Array<{ title: string; ingredients: string; servings: string; instructions: string }>>([]);

// Get userId from Clerk
const { userId } = useAuth();

// Fetch recipe data function
const fetchRecipeData = async () => {
  if (userId.value) {
    try {
      const response = await fetch('https://api.api-ninjas.com/v1/recipe?query=italian', {
        method: 'GET',
        headers: {
          'X-Api-Key': 'a6XoEqfk5aLMbvunPiL9Eg==StLX8STvk7zjSPfk'
        },
      });
      if (!response.ok) {
        throw new Error('Failed to fetch recipe data');
      }
      const data = await response.json();
      recipeData.value = data;
      console.log("DATA", recipeData.value);
    } catch (error) {
      console.error('Error fetching recipe data:', error);
      recipeData.value = [];
    }
  }
};

// Fetch recipe data when the component is mounted and the user is logged in
onMounted(() => {
  if (userId.value) {
    fetchRecipeData();
  }
});
</script>
