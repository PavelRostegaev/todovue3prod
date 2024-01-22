<template>
    <footer class="app-footer">
        Активные задачи: {{ statsTodo?.active}},<br>
        Завершенные задачи: {{ statsTodo?.done}}</footer>
</template>
    
<script lang='ts'>
import { PropType, defineComponent } from 'vue';

export interface Stats {
    active: number,
    done: number,
}

export default defineComponent({
    props: {
        statsTodo: {
            type: Object as PropType<Stats>,
            requaired: true
        }
    }
}) 
    
</script>
    
<style>
    
</style>