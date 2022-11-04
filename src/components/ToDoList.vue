<script>
    export default {
        data() {
            return {
                toDoList: [
                    {text: "Learn Vue.js", isDone: true},
                    {text: "Make a to do list app", isDone: true}
                ],
                todo: null,
                isDoneHidden: false
            }
        },
        computed: {
            filteredToDoList() {
                return !this.isDoneHidden ? this.toDoList : this.toDoList.filter(v=>v.isDone == false)
            }
        },
        methods: {
            addToDo() {
                if(this.toDo) {
                    this.toDoList.push({text: this.toDo, isDone: false})
                    this.toDo = null
                }
            },
            deleteTodo(idx) {
                this.toDoList.splice(idx, 1)
            },
        }
    }
</script>

<template>
    <div class="todo-list-container">
        <h1>To Do List (Vue.js)</h1>
        <input type="text" v-model="toDo" @keyup.native.enter="addToDo" class="input" placeholder="your to do here...">
        <button @click="addToDo">Add To Do</button>
        <div class="helper">
            Press enter or click "Add To Do" button to add to do to the list
        </div>
        <ul>
            <li v-for="(d,idx) in filteredToDoList">
                <input type="checkbox" v-model="d.isDone" :id="'checkbox-'+idx">
                <label :for="'checkbox-'+idx"></label>
                <span :class="'todo-text'+(d.isDone ? ' done':'')">{{ d.text }}</span>
                <span @click="deleteTodo(idx)" class="delete-todo" title="Hapus?">X</span>
            </li>
        </ul>

        <!-- <input type="checkbox" v-model="isDoneHidden" id="hide-done">
        <label for="hide-done">Hide done?</label> -->
    </div>
</template>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');
    * {
        margin: .5em auto;
        word-break: break-all;
    }
    body {
        margin: 1em;
    }
    .todo-list-container{
        font-family: 'Press Start 2P', cursive;
        text-align: center;
        padding: 1.5em;
        border: 1px solid grey;
        background-color: azure;
        border-radius: 1em;
        box-shadow: 1em 1em 0 black;
        font-size: 14px;
    }
    .helper {
        font-size: 80%;
        color: rgba(0,0,0,.5);
        margin: 1em auto;
    }
    input[type="checkbox"] {
        display: none;
    }
    input[type="checkbox"] + label {
        min-width: 2em;
        min-height: 2em;
        border: 1px solid black;
        border-radius: .25em;
        transition: .25s;
        position: relative;
    }
    input[type="checkbox"]:checked + label::after {
        content: "";
        position: absolute;
        left: 50%;
        top: 50%;
        width: .5em;
        height: 1em;
        border: solid white;
        border-width: 0 .25em .25em 0;
        transform: translate(-50%, -50%) rotate(45deg);
    }
    input[type="checkbox"] + label:hover {
        cursor: pointer;
        background-color: rgba(0,0,0,.25);
    }
    input[type="checkbox"]:checked + label {
        background-color: black;
        color: white;
    }
    .input {
        font-family: 'Press Start 2P', cursive;
        background-color: rgba(0,0,0,0);
        border: none;
        border-bottom: 1px solid black;
    }
    button {
        font-family: 'Press Start 2P', cursive;
        background-color: rgba(0,0,0,0);
        border: 1px solid black;
        font-weight: bold;
        transition: .25s;
    }
    button:hover {
        background-color: lightgray;
        cursor: pointer;
    }
    .input:focus {
        outline: none;
    }
    .input::placeholder {
        font-family: 'Press Start 2P', cursive;
    }
    ul {
        text-align: left;
        margin: 0;
        padding: 0;
    }
    li {
        list-style: none;
        display: flex;
        width: 100%;
        align-items: center;
        border-bottom: 1px solid black;
    }
    .todo-text {
        padding: .5em;
        flex-grow: 1;
        margin: 0 .25em;
    }
    .delete-todo {
        padding: .25em .5em;
        margin-left: auto;
        font-weight: bold;
        transition: .25s;
    }
    .delete-todo:hover {
        cursor: pointer;
        color: red;
    }
    .done {
        position: relative;
        color: white;
        z-index: 1;
    }

    .done::after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: black;
        animation: strikethrough .25s ease-in-out;
        z-index: -1;
    }

    @keyframes strikethrough {
        0% {
            width: 0;
        }
        100% {
            width: 100%;
        }
    }
</style>