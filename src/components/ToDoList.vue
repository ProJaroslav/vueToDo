<template>
    <div class="">
        <ul>
            <li v-for="(item, index) in toDos" :key="index">
                <ToDoItem
                    :item="item"
                    @deleteItem="deleteItem"
                    @checkItem="checkItem"
                />
            </li>
        </ul>
        <button @click="increment">CLICK</button>
    </div>
</template>

<script>
import ToDoItem from "./ToDoItem.vue";

export default {
    name: "ToDoList",
    props: {},
    components: {
        ToDoItem,
    },

    data() {
        return {
            toDos: [],
        };
    },

    methods: {
        increment() {
            this.toDos.push("1");
        },

        getIndexInTodos(id) {
            let index = -1;
            for (let i = 0; i < this.toDos.length; i++) {
                if (this.toDos[i].id === id) {
                    index = i;
                    break;
                }
            }
            return index;
        },

        deleteItem(id) {
            const index = this.getIndexInTodos(id);
            this.toDos.splice(index, 1);
        },
        checkItem(id) {
            const index = this.getIndexInTodos(id);
            this.toDos[index].isDone = !this.toDos[index].isDone;
        },
    },
    async mounted() {
        const response = await fetch(
            "https://api.fake.rest/189bf93b-4d78-4f00-86ac-76d87cfccbd1/task/list?fbclid=IwAR3reR0zbxAXhh_joXROTwrHCr7BKuXOj5eis2g98RHqksmL8rgQJMcYSTQ"
        );
        const json = await response.json();
        for (const item of json.data) {
            this.toDos.push(item);
        }
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
