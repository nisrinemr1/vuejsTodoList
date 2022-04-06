<template>
    <div class="todo">
        <div class="content">
            <!-- ************ TITLE ************-->
            <!-- ************ TITLE ************-->
            <!-- ************ TITLE ************-->
            <h1 class="title">My Todo</h1>

            <!-- ************ LIST ************-->
            <!-- ************ LIST ************-->
            <div class="searchBar">
                <input class="avenir" type="text" placeholder="Rechercher une tâche" />
            </div>
            <div class="categories">
                <button class="btn">Urgent</button>
                <button class="btn">Important</button>
                <button class="btn">Pas important</button>
            </div>
            <div class="tasks">
            <div v-for="item in todo" :key="item.name" class="taskItem">
                <!-- get the name from the list_task  -->
                <input class="avenir" type="checkbox" />
                <h3>{{ item.name }}</h3>
                <!-- to show up the item name -->
                <br />
                <p class="importance">{{ item.importance }}</p>
            </div>
            </div>

            <!-- ************ FORM ************-->
            <!-- ************ FORM ************-->
            <!-- ************ FORM ************-->
            <Form :class="'todo-form' + show_form" v-if="show_form" :show.sync="show_form" @addTask="addTask" :addTask.sync="tasks"/>

            <!-- ************ SHOW FORM BUTTON ************-->
            <!-- ************ SHOW FORM BUTTON ************-->
            <!-- ************ SHOW FORM BUTTON ************-->
            <button class="show-form-btn" v-else @click="show_form = true">+</button>
        </div>
    </div>
</template>

<script>
import Form from "./todo/form.vue";

export default {
    name: "Todo-Page",
    components: {
        Form
    },

    props:{
        task: Array
    },

    data() {
        return {
            todo: [{
                id: this.id,
                name: this.name,
                category: this.category,
                isdone: this.isdone
            }],
            
            show_form: false
        };
    },
    methods:{
        newTask(task){
            this.todo = [...this.todo, task],
            console.log("Le tableau est bien transféré")
        }
    }
};
</script>

<style lang="scss">
    .todo {
        height: 100vh;
        width: 100vw;
        display: flex;
        align-items: center;
        justify-content: center;
        flex: 1;

        .content {
            height: 90vh;
            width: 90vw;

            .title {
            padding-top: 30px;
            padding-bottom: 40px;
            text-align: center;
            }

            .searchBar input{
            margin-bottom: 50px;
            width: 98%;
            padding-top: 20px;
            padding-bottom: 20px;
            padding-left: 20px;
            border-radius: 40px;
            background-color: rgb(253, 197, 207);
            border: none;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
            }

            .categories{
                display: flex;
                justify-content: space-between;
                
                & button{
                    background-color: rgba(250, 195, 205, 0.394);
                    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
                }

                button:hover{
                    background-color: rgb(254, 212, 220);
                }

            }

            .taskItem{
                border:1px solid rgb(253, 197, 207);
                border-radius: 10px;
                padding: 5px;
            }

            .importance{
                margin-left: 50%;
                margin-top: 6%;
            }

            .todo-form{
                transition: all .7s ease-in-out;

                .todo-form.true{
                    height: 100px;
                }

                .todo-form.false{
                    height: 0;
                }
            }

            .show-form-btn{
                position: absolute; 
                bottom: 0;
                right: 0;
                margin-bottom: 70px;
                margin-right: 20px;
                padding-left: 20px;
                padding-right: 20px;
                padding-top: 5px;
                padding-bottom: 10px;
                border-radius: 50%;
                font-size: 2rem;
                border: none;
                background-color: rgba(255, 255, 255, 0.845);
            }
        }
    }

/* ********************* */
    .avenir {
        font-family: Avenir, Helvetica, Arial, sans-serif;
    }

    .title {
        padding-top: 30px;
        padding-bottom: 10px;
        text-align: center;
    }
    .todoList {
        width: 100%;
        display: flex;
        justify-content: center;
        align-content: space-between;
        width: 100%;
        height: 75%;
    }

    .listPart {
        width: 50%;
    }

    .todoForm {
        width: 40%;
        height: 100%;
        text-align: center;
        padding-left: 20px;
    }

    .btn {
        background-color: white;
        padding: 10px 10px 10px 10px;
        border-radius: 20px;
        border: 0;
        margin-bottom: 20px;
    }

    .taskItem {
        display: flex;
    }
</style>