<template>
  <a class="flex-it items-start flex-grow w-full" :href="href">
    <div
      class="p-3 flex-row justify-center items-center flex-it rounded-3xl hover:bg-gray-800 hover:rounded-3xl transition duration-200"
    >
      <div class="flex-it">
        <Icon :icon="icon" width="1.5em" height="1.5em" />
      </div>
      <div class="mx-4 text-2xl truncate xl:block hidden">
        <span class="truncate">{{ text }}</span>
      </div>
    </div>
  </a>
</template>

<script setup>
import { Icon } from '@iconify/vue'

// import Icon from './Icon.vue' // adjust path if necessary
defineProps({
  href: String,
  icon: Object,
  text: String,
})
</script>
