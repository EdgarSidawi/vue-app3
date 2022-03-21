<template>
  <div>
    <div  v-for="(list,index) in lists" :key="index">
      <li @click="deleteTodo(index)">
            {{list}}
      </li>
    </div>
  </div>
</template>

<script>

export default {
  name: 'TodoList',
  props: ['lists'],

  setup(_, context) {

    function deleteTodo(index) { 
     context.emit("deleteItem",index)
    }
    return{
      deleteTodo
    }
  }
}
</script>