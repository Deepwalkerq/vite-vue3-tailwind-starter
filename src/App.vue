<script setup>
import { ref, onMounted } from 'vue'
import { BadgeCheckIcon } from '@heroicons/vue/solid'

const time = ref(null)

const startTime = function(){
  const today = new Date();
  let h = today.getHours();
  let m = today.getMinutes();
  let s = today.getSeconds();
  m = checkTime(m);
  s = checkTime(s);
  time.value =  h + ":" + m + ":" + s;
  setTimeout(startTime, 1000);
}

const checkTime = function(i) {
  if (i < 10) {i = "0" + i}  // add zero in front of numbers < 10
  return i;
}

onMounted(() => {
  startTime()
})
</script>

<template>
  <!-- <div>
    <header class="bg-white shadow" v-if="$route.meta.title">
  </div> -->
  <div class="h-min-screen w-min-screen">
    <header class="md:h-24 min-w-max p-0 md:p-2 shadow bg-slate-200 dark:bg-slate-800">
      <div class="flex flex-auto items-center min-w-sm justify-center md:justify-start">
        <h1 class="md:text-2xl dark:text-slate-200">123</h1>
        <h2 class="text-sm dark:text-slate-200">245</h2>

      </div>
    </header>
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>
