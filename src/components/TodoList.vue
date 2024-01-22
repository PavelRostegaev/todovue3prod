<template>
    <ul class="todo-list">
        <TodoItem 
            v-for="todo in todosList" 
            :todoItem="todo"
            :key="todo.id"
            @toogleTodo="toogleTodo"
            @removeTodo="removeTodo"
        />
    </ul>
</template>
    
<script lang='ts'>
import { defineComponent, PropType} from "vue";
import TodoItem from "@/components/TodoItem.vue"
import { Todo } from '@/types/Todo'

export default defineComponent ({
  components: {
    TodoItem,
  },
  props: {
    todosList: {
        type: Array as PropType<Todo[]> ,
    }
  },
  methods: {
        toogleTodo(id: number){
            this.$emit('toogleTodo', id)
        },
        removeTodo(id: number){
            this.$emit('removeTodo', id)
        },
    },
 
})
</script>
    
<style>
    
</style>