<script setup>
const props = defineProps({
  books: Object
});
</script>

<template>
  <div>
    <div v-for="(items, group) in books" :key="group" class="group">
      <h3>{{ group }}</h3>
      <ul>
        <li v-for="(b, index) in items" :key="index">
          <strong>{{ b.title }}</strong> — {{ b.authorFirst }} {{ b.authorLast }} ({{ b.year }})
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.group { margin-bottom: 20px; }
</style>
