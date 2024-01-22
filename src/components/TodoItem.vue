<template>
    <li 
        class="todo-item" 
        :class="{'todo-item--done': todoItem.done}"
        @click="toogleTodo"
    >
        <div class="todo-item__status">
            <i class="bi bi-check2"></i>
        </div>
        <span class="todo-item__text">{{todoItem.text}}</span>
        <button 
            class="todo-item__remove-button"
            @click.stop="removeTodo"
        >
            <i class="bi bi-trash3"></i>
        </button>
    </li>
</template>
    
<script lang='ts'>
import { PropType, defineComponent } from 'vue';
import { Todo } from '@/types/Todo'

export default defineComponent({
    props: {
        todoItem: {
            type: Object as PropType<Todo>,
            required: true,
        }
    },
    methods: {
        toogleTodo(){
            this.$emit('toogleTodo', this.todoItem.id)
        },
        removeTodo(){
            this.$emit('removeTodo', this.todoItem.id)
        },
    },
})
</script>
    
<style>
    
</style>