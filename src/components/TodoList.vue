<template>
    <section class="todo__container">
        <!-- <ul class="todo__list"> -->
        <transition-group class="todo__list" name="list" tag="ul">
            <li class="todo__item shadow" v-for="(todoItem, index) in propsdata" :key="todoItem">
                <i class="check-icon fas fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="remove-btn" type="button" v-on:click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
        <!-- </ul> -->
    </section>
</template> 

<script>
export default {
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
        }
    }
}
</script>

<style lang="scss">
    .todo__list {margin-top:0;padding-left:0;list-style-type:none}
    .todo__item {display:flex;overflow:hidden;min-height:50px;height:50px;margin:0.5rem 0;padding:0 0.9rem;border-radius:5px;text-overflow:ellipsis;white-space:nowrap;line-height:50px;background:#fff}
    .check-icon {margin-right:8px;line-height:45px;color:#62acde}
    .remove-btn {margin-left:auto;color:#de4343}

    .list-enter-active,
    .list-leave-active {transition:all 1s}
    .list-enter,
    .list-leave-to {opacity:0;transform:translateY(30px)}
</style>