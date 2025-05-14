<template>
  <div class="flex-it p-4 border-b-1 border-solid border-gray-700">
    <div class="flex-it flex-row">
      <div class="flex-it mr-4">
        <div class="w-12 h-12 overflow-visible cursor-pointer transition duration-200 hover:opacity-80">
          <img
            class="rounded-full"
            :src="glide.user.avatar"
            alt="avatar"
          />
        </div>
      </div>
      <article class="flex-it flex-grow flex-shrink cursor-pointer">
        <div class="flex-it justify-center flex-grow mb-1">
          <div class="flex-it justify-between flex-row w-full">
            <div>
              <span class="font-bold">{{ glide.user.nickName }}</span>
              <span class="mx-2">&#8226;</span>
              <span class="text-gray-400">{{ relativeTime }}</span>
            </div>
            <div class="text-gray-400 cursor-pointer transition hover:text-red-400">
              <FiTrash :size="16" />
            </div>
          </div>
        </div>
        <div class="flex-it flex-row flex-grow-0 items-center mb-2">
          <div class="flex-it mr-3 mb-3 w-full">{{ glide.content }}</div>
        </div>
        <div class="flex-it flex-row flex-grow text-gray-400">
          <div class="flex-it flex-row items-center cursor-pointer mr-5 transition hover:text-blue-400">
            <AiOutlineMessage :size="18" />
            <span class="text-xs ml-3">{{ glide.subglidesCount }}</span>
          </div>
          <div class="flex-it flex-row items-center cursor-pointer transition hover:text-pink-400">
            <FaHeart :size="18" />
            <span class="text-xs ml-3">{{ glide.likesCount }}</span>
          </div>
        </div>
      </article>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { AiOutlineMessage } from 'vue3-icons/ai'
import { FaHeart } from 'vue3-icons/fa'
import { FiTrash } from 'vue3-icons/fi'

interface Glide {
  id: string
  content: string
  date: Date
  likesCount: number
  subglidesCount: number
  user: {
    nickName: string
    avatar: string
  }
}

const props  = defineProps<{ glide: Glide }>()


const relativeTime = computed(() => {
  const diff = (new Date().getTime() - new Date(props.glide.date).getTime()) / 1000
  if (diff < 60) return 'just now'
  if (diff < 3600) return `${Math.floor(diff / 60)}m ago`
  if (diff < 86400) return `${Math.floor(diff / 3600)}h ago`
  return `${Math.floor(diff / 86400)}d ago`
})
</script>
