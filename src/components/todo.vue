<template>
    <div class="todo">
        <div class="content">
            <!-- ************ TITLE ************-->
            <!-- ************ TITLE ************-->
            <!-- ************ TITLE ************-->
            <h1 class="title">My Todo</h1>

            <!-- ************ LIST ************-->
            <!-- ************ LIST ************-->
            <!-- ************ LIST ************-->
            <div class="searchBar">
                <input class="avenir" type="text" placeholder="Rechercher une tâche" />
            </div>
            <div v-show="false" class="categories">
                <button class="btn">Urgent</button>
                <button class="btn">Important</button>
                <button class="btn">Pas important</button>
            </div>


            <div v-for="(item, index) in list" :key="item.name" class="task-items">
                <!-- get the name from the list_task  -->
                <div>
                    <input class="avenir" type="checkbox"/>
                    <p>{{index}}</p>
                </div>
                <h3>{{ item.name }}</h3>
                <!-- to show up the item name -->
                <br />
                <p class="importance">{{ item.category }}</p>
                <button class="delete">delete</button>
            </div>

            <!-- ************ FORM ************-->
            <!-- ************ FORM ************-->
            <!-- ************ FORM ************-->
            <!-- <Form :class="'todo-form' + show_form" v-if="show_form" :show.sync="show_form" @addTask="addTask" :addTask.sync="tasks"/> -->
            <div v-if="show_form" class="form">

                <!-- CLOSE FORM BUTTON -->
                <button class="close-form-btn" @click="close">X</button>


                <form @submit.prevent="add">


                    <!-- LABEL -->
                    <label>Tâche: </label>


                    <!-- NAME -->
                    <input class="avenir" placeholder="Ajouter une tâche" v-model="todo.name" id="idTask" name="name" />


                    <!-- CATEGORY -->
                    <select v-model="todo.category" name="importance">
                        <option disabled>Importance</option>
                        <option value="urgent">Urgent</option>
                        <option value="important">Important</option>
                        <option value="pasimportant">Pas important</option>
                    </select>


                    <!--  CATEGORY -->
                    <button type="submit">Ajouter</button>


                </form>
            </div>

            <!-- ************ SHOW FORM BUTTON ************-->
            <!-- ************ SHOW FORM BUTTON ************-->
            <!-- ************ SHOW FORM BUTTON ************-->
            <button class="show-form-btn" v-else @click="show_form = true">+</button>


        </div>
    </div>
</template>

<script>
    export default {
        name: "Todo-Page",
        components: {},

        props: {
            id: Number,
            name: String,
            category: String,
            isdone: Boolean
        },

        data() {
            return {
                todo: {
                    name: "",
                    category: "testcateg",
                    isdone: null
                },
                /* Objet */
                list: [{
                    name: "test",
                    category: "urgent",
                    isdone: false
                }],
                /* Ma liste (array) */

                show_form: false,

                test: "first"
            };
        },
        methods: {
            close() {
                this.show_form = false
            },
            add() {
                this.list.push({
                    name: this.todo.name,
                    category: this.todo.category
                })
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

            .searchBar input {
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

            .categories {
                display: flex;
                justify-content: space-between;

                & button {
                    background-color: rgba(250, 195, 205, 0.394);
                    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
                }

                button:hover {
                    background-color: rgb(254, 212, 220);
                }

            }


            .task-items {
                width: 100%;
                display: flex;
                justify-content: space-between;
                align-items: center;
                border: 1px solid rgb(253, 197, 207);
                border-radius: 10px;
                padding: 5px;

                & div{
                    display: flex;
                }
            }



            .todo-form {
                transition: all .7s ease-in-out;

                .todo-form.true {
                    height: 100px;
                }

                .todo-form.false {
                    height: 0;
                }
            }

            .show-form-btn {
                position: absolute;
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
                bottom: 0;
                right: 0;
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

    /* *********************************** */
    .form {
        overflow: hidden;
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100vw;
        display: flex;
        justify-content: end;
        flex-direction: row-reverse;
        background-color: white;
        padding-top: 20px;
        padding-bottom: 30px;

        .close-form-btn {
            margin-bottom: 60px;
            margin-right: 40px;
            border: none;
            font-size: 1.1rem;
            background-color: white;
        }

        form {
            padding-top: 40px;

            label {
                padding-right: 15px;
            }

            input {
                margin-right: 15px;
                border-radius: 20px;
                background-color: rgb(253, 197, 207);
                border: none;
                padding-top: 5px;
                padding-bottom: 5px;
                padding-left: 15px;
                box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
            }

            select {
                margin-right: 15px;
                padding-top: 5px;
                padding-bottom: 5px;
                padding-left: 5px;
                padding-right: 5px;
                background-color: rgb(253, 197, 207);
                border: none;
                border-radius: 20px;
                box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
            }

            button {
                padding-top: 10px;
                padding-bottom: 10px;
                padding-left: 10px;
                padding-right: 10px;
                background-color: rgb(253, 197, 207);
                border: none;
                border-radius: 20px;
                box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
            }

            button:hover {
                background-color: rgb(254, 212, 220);
            }

        }
    }
</style>