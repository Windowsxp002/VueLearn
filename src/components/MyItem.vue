<template>
    <li>
        <label>
            <input type="checkbox" :checked="todoItem.completed" @click="handleCheck(todoItem.id)" />
            <span>{{ todoItem.title }}</span>
        </label>
        <button class="btn btn-danger" @click="handleDelete(todoItem.id)">删除</button>
    </li>
</template>

<script>
export default {
    name: 'MyItem',
    props: ['todoItem','changeItem','deleteItem'],
    methods: {
        handleCheck(id){
            console.log('@@',id)
            this.changeItem(id)
        },
        handleDelete(id){
            this.deleteItem(id)
        }
    },
}
</script>

<style scoped>
/*item*/
li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
}

li label {
    float: left;
    cursor: pointer;
}

li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
}

li button {
    float: right;
    display: none;
    margin-top: 3px;
}

li:before {
    content: initial;
}

li:last-child {
    border-bottom: none;
}
li:hover{
    background-color: #4cc2ff;
}
li:hover button{
    display: block;
}
</style>