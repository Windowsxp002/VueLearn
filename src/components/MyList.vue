<template>
    <ul class="todo-main">
        <MyItem v-for="todoItem in todos" :key="todoItem.id" :todoItem="todoItem" :changeItem="changeItem" :deleteItem="deleteItem"/>
    </ul>
</template>

<script>
import MyItem from './MyItem.vue'
export default {
    name: 'MyList',
    components: {
        MyItem
    },
    props:['todos','changeItem','deleteItem']
}
</script>

<style scoped>
/*main*/
.todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
}

.todo-empty {
    height: 40px;
    line-height: 40px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-top: 10px;
}
</style>