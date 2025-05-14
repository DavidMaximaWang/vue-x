<template>
  <div class="bg-gray-800 overflow-hidden flex-it rounded-2xl">
    <div class="flex-it p-4">
      <span class="text-xl font-bold">Trends</span>
    </div>
    <div v-for="(trend, index) in trends" :key="index" class="flex-it p-4 cursor-pointer transition duration-200 hover:bg-gray-700">
      <div class="flex-it">
        <span class="text-gray-400 text-sm">{{ trend.content }}</span>
        <span class="text-lg font-bold">{{ trend.category }}</span>
        <span class="text-gray-400 text-sm">{{ trend.glideCount.toLocaleString() }} Glides</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      trends: [
        {
          category: 'Sports',
          content: 'Some team won something!',
          glideCount: this.randomize()
        },
        {
          category: 'Finance',
          content: 'Bitcoin down again!',
          glideCount: this.randomize()
        },
        {
          category: 'PC & Games',
          content: 'New Eincode game out!',
          glideCount: this.randomize()
        },
        {
          category: 'Economy',
          content: "It's goin well...",
          glideCount: this.randomize()
        },
        {
          category: 'Celebrities',
          content: 'Some useless news!',
          glideCount: this.randomize()
        },
        {
          category: 'Movies',
          content: 'Peter Jackson as the director of new Lotr',
          glideCount: this.randomize()
        }
      ]
    };
  },
  methods: {
    randomize() {
      return Math.floor(Math.random() * 500);
    }
  }
};
</script>

<style scoped>
/* Add any additional styles you need */
</style>
