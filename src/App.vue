<script setup lang="ts">
import Button from './components/ui/button/Button.vue';

defineProps<{ msg: string }>()

</script>

<template>
  <h1 class="text-white">{{ msg }}</h1>
  <div class="w-full h-screen bg-stone-900 flex justify-evenly items-center">
    <div class="w-2/4 h-1/4 border-solid border-2 border-white rounded-lg">
      <p class="text-white m-2">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.</p>
    </div>
    <div class="w-1/4 h-1/4 border-2 border-white rounded-lg">
      <p></p>
    </div>
  </div>
  <App msg="TITRE HELLOWORD COMPONENT" />
</template>

