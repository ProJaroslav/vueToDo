<template>
    <div class="">
        <ul>
            <li v-for="(item, index) in toDos" :key="index">
                <ToDoItem :item="item" @deleteItem="deleteItem" />
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
            toDos: [
                {
                    id: "1",
                    text: "todo",
                },
                {
                    id: "2",
                    text: "todo2",
                },
            ],
        };
    },

    methods: {
        increment() {
            this.toDos.push("1");
        },

        deleteItem(id) {
            let index = -1;
            for (let i = 0; i < this.toDos.length; i++) {
                if (this.toDos[i].id === id) {
                    index = i;
                    break;
                }
            }
            this.toDos.splice(index, 1);
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
