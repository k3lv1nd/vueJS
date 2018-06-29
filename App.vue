<template>
    <div id="app" style="align-content: center;">

        <input type="text" v-model="newTask.name" style="margin-left: 500px;">
        <button v-bind:class="{alert:isready}" type="button>" @click="addTask">Add To do</button>

        <h1 style="text-align: center">List of to do items</h1>
        <ul v-for="(task, index) in tasks" style="margin-left: 500px">
            <li> {{task.name}} &nbsp;
                <button type="button" @click="deleteTask(index)" style="margin-left: 10px">Delete</button>
            </li>
        </ul>
        <hr>
        <h3>Components</h3>
        <v-button :onClick="buttonClick"></v-button>
        <hr>
        <h3>message passing</h3>
        <v-messagepass @send-message="updateMessage"></v-messagepass>

    </div>

</template>

<script>
    import button from '../src/components/button.vue'
    import messagepassing from '../src/components/messagepassing.vue'
    export default {
        name: 'app',
        data(){
            return {
                newTask: {},
                message: "hello man",
                tasks: [{
                    name: "kuku",
                },],
                isready: true
            }
        },
        components:{
            'v-button': button,
            'v-messagepass' :messagepassing

        },
        methods: {
            addTask(){
                if (this.newTask == '') {
                    alert('enter a task please');
                } else {
                    this.tasks.push(this.newTask);
                    //alert("adding to do")
                }
            },
            
            buttonClick (){
                alert('button has been clicked');
            },
            deleteTask(index){
                this.tasks.splice(index, 1);

            }
        },
        mounted (){
            //alert ("ready");
        }
    }
</script>

<style>
    .alert {
        background: green;
    }
</style>