<template>
    <div>
        <div class="todo">
            <h1 class="title">My TodoList</h1>
            <div class="todoList">
                <div class="listPart">
                    <task-list/>
                </div>
                <div class="todoForm">
                    <button v-on:click="isHiddenForm = !isHiddenForm">+</button>
                    <!-- sync permet de donner l'autorisation à l'enfant de modifier le parent -->
                </div>
            </div>
            <div :class=" 'form ' + isHiddenForm ">
                <add-task-form/>
            </div>
        </div>
    </div>
</template>

<script>
import AddTaskForm from './addTaskForm.vue';
import taskList from './taskList.vue';
export default {
    components: { taskList, AddTaskForm },
    name: "TodoList",
    data(){
        return{
            isHiddenForm: false,
        }
    },
    methods: {
        add: function(){
            this.list_task.push({name: "Hellow"})
            console.log(this.list_task)
        } 
    }
};
</script>

<style>
.todo { 
    background-color: #bc8f8f;
    height: 90vh;
}

.avenir{
    font-family: Avenir, Helvetica, Arial, sans-serif;
}

.title{
    padding-top: 30px;
    padding-bottom: 10px;
    text-align: center;
}
.todoList{
    width: 100%;
    display: flex;
    justify-content: center;
    align-content: space-between;
    width: 100%;
    height: 75%;
}

.listPart{
    width: 50%;
}

.todoForm{
    width: 40%;
    height: 100%;
    text-align: center;
    padding-left: 20px;
}

.btn{
    background-color: #af6a7e;
    padding: 5px 5px 5px 5px;
    border-radius: 5px;
    border: 0; 
    margin-bottom: 20px;
}

.taskItem{
    display: flex;
}

.form{
    text-align: end;
    padding-right: 3%;
    transition: all .7s ease-in-out;
    overflow: hidden;
}

.form.true{
    height: 100px;
}

.form.false{
    height: 0px;
}


</style>