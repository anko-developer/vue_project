<template>
    <div class="todo__clear-wrap">
        <p class="todo__clear-btn" v-on:click="clearTodo">Clear All</p>
    </div>
</template>

<script>
export default {
    methods: {
        clearTodo() {
            this.$emit('removeAll');
        }
    }
}
</script>

<style lang="scss">
    .todo__clear-wrap {width:8.5rem;height:50px;margin:0 auto;border-radius:5px;line-height:50px;background-color:#fff}
    .todo__clear-btn {text-align:center;color:#e20303}
</style>