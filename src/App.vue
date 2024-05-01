<template>
  <textarea v-model="input"></textarea>
  <div class="vbar"></div>
  <section class="timeline">
    <div v-for="el of output" class="entry">
      <div class="line"></div>
      <div class="data">
        <span class="date">{{ el.date }}</span>
        <span class="caption">{{ el.caption }}</span>
      </div>
      <div class="line"></div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';

const parseLine = (input: string) => {
  const [date, caption] = input.split(/: ?/);
  return { date, caption };
};

const input = ref('');
const output = computed(() => input.value.split('\n').map(parseLine));
</script>
