<template>
    <div id="root">
        <div class="todo-container">
            <div class="todo-wrap">
                <MyHeader :addTodo='addTodo' />
                <MyList :todos='todos' :checkTodo='checkTodo' :deleteTodo="deleteTodo" />
                <MyFooter :todos='todos' :checkAllTodo='checkAllTodo' :clearAllTodo='clearAllTodo' />
            </div>
        </div>
    </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import MyFooter from "./components/MyFooter.vue";
import MyList from "./components/MyList.vue";
export default {
    name: 'App',
    components: { MyHeader, MyFooter, MyList },
    data() {
        return {
            todos: [
                { id: '001', title: '抽烟', done: true },
                { id: '002', title: '喝酒', done: false },
                { id: '003', title: '开车', done: true }
            ]
        }
    },
    // 数据在哪个组件中  对于数据的操作就写在哪里
    methods: {
        // 添加一个todo
        addTodo(item) {
            this.todos.unshift(item)
        },
        // 勾选或取消勾选一个todo
        checkTodo(id) {
            this.todos.forEach(todo => {
                if (todo.id === id) todo.done = !todo.done
            });
        },
        // 删除一个todo
        deleteTodo(id) {
            this.todos = this.todos.filter(todo => todo.id !== id)
        },
        // 全选or取消全选
        checkAllTodo(done) {
            this.todos.forEach(todo => todo.done = done)
        },
        // 清除所有已经完成的todo
        clearAllTodo() {
            this.todos = this.todos.filter(todo => !todo.done)
        }
    },
}
</script>

<style>
body {
    background: #fff;
}

.btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
}

.btn-danger {
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
}

.btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
}

.btn:focus {
    outline: none;
}

.todo-container {
    width: 600px;
    margin: 0 auto;
}

.todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
}

/*header*/
.todo-header input {
    width: 560px;
    height: 28px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 4px 7px;
}

.todo-header input:focus {
    outline: none;
    border-color: rgba(82, 168, 236, 0.8);
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}

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