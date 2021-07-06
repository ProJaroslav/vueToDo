<template>
    <div class="">
        <span :class="isChecked ? `line-through` : ``">{{ item.text }}</span>
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
        return {
            isChecked: false,
        };
    },
    methods: {
        check() {
            this.isChecked = !this.isChecked;
        },

        deleteSelf() {
            this.$emit("deleteItem", this.item.id);
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
