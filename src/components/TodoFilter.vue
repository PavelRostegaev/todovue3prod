<template>
    <aside class="app-filters">
    <section class="toggle-group">
        <button 
            class="button"
            :class="{'button--primary' : selectFilter === 'All'}"
            @click="() => setFilter('All')"
        >Все
        </button>
        <button 
            class="button"
            :class="{'button--primary' : selectFilter === 'Active'}"
            @click="setFilter('Active')"
        >Активные
        </button>
        <button 
            class="button"
            :class="{'button--primary' : selectFilter === 'Done'}"
            @click="setFilter('Done')"
        >Завершенные
        </button>
    </section>
    </aside>  
</template>
    
<script lang='ts'>
import { PropType, defineComponent } from 'vue';

export default defineComponent({
    props: {
        selectFilter: {
            type: String as PropType<'All' | 'Active' | 'Done'>,
            required: true,
        }
    },
    methods: { 
        setFilter(select: string){
            this.$emit('setFilter', select)
        }
    },
})
</script>
    
<style>
    
</style>