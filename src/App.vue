<template>
    <div id="app">
      <TodoHeader />

      <TodoFilter 
        @setFilter="changeFilter"
        :selectFilter="selectFilter"
      />

      <main class="app-main">
        
        <TodoList 
          :todosList="filteredList"
          @toogleTodo="toogleTodo"
          @removeTodo="removeTodo"
        />

        <TodoAddTodo 
          @newAdd="newAdd"
        />
        
      </main>

      <TodoFooter 
        :statsTodo="statsTodo"
      />
    </div>
</template>
  
<script lang='ts'>
import { defineComponent } from "vue";
import TodoHeader from "@/components/TodoHeader.vue"
import TodoFilter from "@/components/TodoFilter.vue"
import TodoList from "@/components/TodoList.vue"
import TodoAddTodo from "@/components/TodoAddTodo.vue"
import TodoFooter, { Stats } from "@/components/TodoFooter.vue"
import { Todo } from '@/types/Todo'

interface ItemTodo {
    todosList: Todo[],
    selectFilter: 'All' | 'Active' | 'Done',
}
export default defineComponent ({
  components: {
    TodoHeader, 
    TodoFilter, 
    TodoList,
    TodoAddTodo,
    TodoFooter,
  },
  data(): ItemTodo {
    return {
        todosList: [
            {id: 0, text: 'Сделать зарядку', done: true},
            {id: 1, text: 'Приготовить кофе', done: false},
            {id: 2, text: 'Выгулять кота', done: false},
            {id: 3, text: 'Забить гвоздь', done: false},
        ],
        selectFilter: 'All',
    }
  },
  methods: {
    toogleTodo(id: number){
        const targetTodo = this.todosList.find((todo: Todo) => todo.id === id)
        if(targetTodo) {
            targetTodo.done = !targetTodo.done
        }
    },
    removeTodo(id: number){
        this.todosList = this.todosList.filter((todo: Todo) => todo.id !== id)
    },
    newAdd(newAdd: Todo){
      this.todosList.push(newAdd)
    },
    changeFilter(filter: any){
      this.selectFilter = filter
    },
  },
  computed: {
    filteredList(): Todo[] {
      switch (this.selectFilter) {
        case 'Active':
          return this.todosList.filter(todo => !todo.done)
        case 'Done':
          return this.todosList.filter(todo => todo.done)
        case 'All':
        default: 
          return this.todosList
      }      
    },
    statsTodo(): Stats {
      return {
        active: this.todosList.filter(todo => !todo.done).length,
        done: this.todosList.filter(todo => todo.done).length
      }
    }
  }
})
</script>
  
<style>
  
</style>