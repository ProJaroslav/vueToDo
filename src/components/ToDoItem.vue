<template>
    <div class="">
        <span :class="decoration">{{ item.name }}</span>
        <button @click="deleteSelf">DELETE</button>
        <button @click="check">CHECK</button>
    </div>
</template>

<script>
export default {
    name: "ToDoItem",
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {};
    },
    methods: {
        check() {
            this.$emit("checkItem", this.item.id);
        },

        deleteSelf() {
            this.$emit("deleteItem", this.item.id);
        },
    },
    computed: {
        decoration() {
            return this.item.isDone ? `line-through` : ``;
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.line-through {
    text-decoration: line-through;
}
</style>
