<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox" v-model="allSelect" />
        </label>
        <span>
            <span>已完成{{ doneNum }}</span> / 全部{{ todos.length }}
        </span>
        <button class="btn btn-danger" @click="clearDone">清除已完成任务</button>
    </div>
</template>

<script>
export default {
    name: 'MyFooter',
    props: ['todos'],
    computed: {
        doneNum() {
            return this.todos.reduce((pre, cur) => pre + (cur.done ? 1 : 0), 0)
        },
        allSelect: {
            get() {
                return this.doneNum === this.todos.length
            },
            set(value) {
                this.$emit('selectAll', value)
            }
        }
    },
    methods: {
        clearDone() {
            this.$emit('deleteAllDone')
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