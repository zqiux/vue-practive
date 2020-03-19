<template>
  <div id="app">
    {{message}}{{message + message}}
    <div v-bind:id="message"></div>
    <todo-list>
        <todo-item @delete="handleClick" v-for="item in list" :key="item.title" :title="item.title" :del="item.del">
            <template v-slot:pre-icon="{value}"><span>前置图标{{value}}</span></template>
            <template v-slot:suf-icon><span>后置图标</span></template>
        </todo-item>
    </todo-list>
    <input type="text" v-model="message">
    <input type="text" :value="message" @input="handleChange">
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  components: {
    TodoList,
    TodoItem
  },
  data(){
    return{
      message: 'hello world',
      list: [{
            title: '课程2',
            del: false
        }, {
            title: '课程3',
            del: true
        }],
      }
    },
    methods: {
          handleClick(val) {
              console.log('handleDelete', val);
          },
          handleChange(e){
            this.message = e.target.value
          }
      }
    
  }
</script>

<style>

</style>
