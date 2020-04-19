<template>
    <div class="todo__input-box">
        <span class="todo-add-btn" v-on:click="addTodo">
            <i class="add-icon fas fa-plus" aria-hidden="true"></i>
        </span>
        <p class="todo__input-wrap">
            <input type="text" class="todo-input" v-model="newTodoItem" v-on:keyup.enter="addTodo" placeholder="Type what you have to do">
        </p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ''
        }
    },
    methods: {
        // addTodo: function() {
        //     console.log(this.newTodoItem);
        // }
        addTodo() {
            if (this.newTodoItem !== '') {
                let value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
            }
        },
        clearInput() {
            this.newTodoItem = '';
        }
    }
}
</script>

<style lang="scss">
    .todo__input-box {overflow:hidden;border-radius:5px;background-color:#fff}
    .todo__input-wrap {overflow:hidden;height:50px;margin:0}
    .todo-input {display:block;width:100%;height:100%;border-style:none;font-size:0.9rem;text-align:center}
    .todo-input:focus {outline:none}
    .todo-add-btn {float:right;width:3rem;border-radius:0 5px 5px 0;line-height:50px;text-align:center;background:linear-gradient(to right, #6478fb, #8763fb)}
    .add-icon {vertical-align:middle;color:#fff}
</style>