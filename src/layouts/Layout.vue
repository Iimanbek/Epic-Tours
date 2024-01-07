<script setup lang="ts">
import {ref, defineComponent} from 'vue'
import Header from '@/components/layOuts/Header.vue'
import Footer from "@/components/layOuts/footer.vue";
</script>
<template>
    <div>
        <Header/>
        <main>
        <slot/>
        </main>
      <Footer/>
    </div>
</template>

