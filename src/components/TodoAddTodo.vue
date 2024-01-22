<template>
    <section class="add-todo">
          <button 
            class="add-todo__show-form-button"
            v-if="!isFormVisible"
            @click="() => isFormVisible = true"
          >
            <i class="bi bi-plus-lg"></i>
          </button>
          <form 
            class="add-todo__form"
            v-if="isFormVisible"
           
          >
            <button 
              class="close-button" 
              type="button"
              @click="() => isFormVisible = false"
            >
              <i class="bi bi-x"></i>
            </button>
            <div class="text-input text-input--focus">
              <input 
                class="input"
                v-model="todoText"
              />
            </div>
           <button 
            class="button button--filled"
            @click.prevent="addTodo"
          >Добавить задачу</button>
          </form>
        </section>
</template>
    
<script lang='ts'>
import { defineComponent } from 'vue';
import { Todo } from '@/types/Todo'

interface State {
  isFormVisible: boolean,
  todoText: string,
}

export default defineComponent({
  data(): State {
    return {
      isFormVisible: false,
      todoText: '',
    }
  },
  methods: {
    addTodo(){
      if(this.todoText !== ''){
        const newAdd: Todo = {
        id: Date.now(),
        text: this.todoText,
        done: false
      }
      this.$emit('newAdd', newAdd)
      this.todoText = ''
      this.isFormVisible = false
      }
    }
  }
})
</script>
    
<style>
    
</style>