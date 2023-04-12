<template>
    <div>
        <input class="inputTodo" type="text" v-model="newTodoText" />
        <button v-on:click="addTodo">Añadir tarea</button>
        <hr>
        <ul>
            <div class="todo" v-for="todo in todos" :key="todo">
                <li>{{ todo.text }}</li>
                <button v-on:click="deleteTodo(todo.id)">Eliminar tarea</button>
            </div>
        </ul>
    </div>
</template>

<script>

let nextTodoId = 1;
export default {
    name: "TodoList",
    components: {},
    data() {
        return {
            todos: [
                { id: nextTodoId++, text: "Todo 1" },
                { id: nextTodoId++, text: "Todo 2" },
                { id: nextTodoId++, text: "Todo 3" },
            ],
        }
    },
    methods: {
        addTodo: function () {
            if (this.newTodoText) {
                const trimmedText = this.newTodoText.trim();
                if (trimmedText) {
                    this.todos.push({
                        id: nextTodoId++,
                        text: trimmedText
                    })
                }
            }
        },
        deleteTodo: function(idToRemove){
           this.todos=this.todos.filter(todo =>{
                return todo.id !== idToRemove;
            })
        },
    },
};
</script>
<style scoped>
.todo {
    display: flex;
    justify-content: center;
    padding: 8px;
}
.inputTodo{
    padding: 16px;
    font-size: 22px;
    width: 30%;
}
</style>
