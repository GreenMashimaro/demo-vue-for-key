<script setup lang="ts">
import { reactive } from 'vue';
import StaticComponent from './components/StaticComponent.vue'

interface PersonItem {
  name: string
}

const list: PersonItem[] = reactive([
  {
    name: 'xiaoming'
  },
  {
    name: 'xiaohong'
  },
  {
    name: 'coco'
  }
])

function clickDeleteItem(item: PersonItem) {
  const index = list.findIndex((ii) => ii === item)
  if (index >= 0) {
    list.splice(index, 1)
  }
}
</script>

<template>
  <div>
    <div>
      <div v-for="(item) in list" @click="clickDeleteItem(item)">
        click me to trigger delete: <StaticComponent :name="item.name" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
