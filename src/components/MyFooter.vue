<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox" :checked="isAllCompleted" @change="selectAllItem" />
        </label>
        <span>
            <span>已完成{{ completedCount }}</span> / 全部{{ todos.length }}
        </span>
        <button class="btn btn-danger">清除已完成任务</button>
    </div>
</template>

<script>
export default {
    name: 'MyFooter',
    props: ['todos','selectAll'],
    computed: {
        completedCount() {
            var result = 0;
            this.todos.forEach((todo) => {
                if (todo.completed) {
                    result++
                }
            });
            return result;
        },
        isAllCompleted() {
            return (this.completedCount == this.todos.length) && (this.todos.length > 0)
        }
    },
    methods: {
        selectAllItem(e) {
            console.log("是否全选:>", e.target.checked)
            this.selectAll(e.target.checked)
        }
    }
}
</script>

<style scoped>
/*footer*/
.todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
}

.todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
}

.todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
}

.todo-footer button {
    float: right;
    margin-top: 5px;
}
</style>