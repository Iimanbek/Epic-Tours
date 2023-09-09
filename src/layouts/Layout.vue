<script setup lang="ts">
import {ref, defineComponent} from 'vue'
import Header from '../components/layOuts/Header.vue'
import Loading from '../components/Loading.vue'
import {lazyLoadComponentIfVisible} from '../utils'

const Lazyfooter = lazyLoadComponentIfVisible({
  componentLoader: () => import('../components/layOuts/footer.vue'),
  loadingComponent: Loading,
});
</script>
<template>
    <div>
        <Header/>
        <main>
            <slot/>
        </main>
        <Lazyfooter/>
    </div>
</template>
<!-- <template>
    <div>
        <v-header/>
        <main>
            <slot/>
        </main>
        <v-footer/>
    </div>
</template>
<script>
import Header from '../components/layOuts/Header.vue'
import Footer from '../components/layOuts/footer.vue'
export default{
    components:{
        'v-header': Header,
        'v-footer': Footer
    }
}
</script> -->