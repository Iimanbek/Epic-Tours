<script setup lang="ts">
import {lazyLoadComponentIfVisible} from '@/utils'
import Loading from "@/components/Loading.vue";
const lazymain = lazyLoadComponentIfVisible({
  componentLoader: () => import('@/components/mainComponents/Welcome.vue'),
  loadingComponent: Loading,
});
const lazymainafter = lazyLoadComponentIfVisible(
    {
      componentLoader: () => import('@/components/mainComponents/texxxt.vue'),
      loadingComponent: Loading,
    }
)
</script>

<template>
  <div>
    <lazymain/>
    <lazymainafter/>
  </div>
</template>


<style scoped>
</style>