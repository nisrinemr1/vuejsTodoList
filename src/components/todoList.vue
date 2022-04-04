<template>
    <div class="todo">
        <h1 class="title">My TodoList</h1>
        <div class="container">
            <div class="todoList">
                <div class="searchBar">
                    <input type="text" placeholder="Rechercher une tâche">
                </div>
                <div class="categories">
                    <button class="btn">Urgent</button>
                    <button class="btn">Important</button>
                    <button class="btn">Pas urgent</button>
                    <button class="btn">Pas important</button>
                </div>
                <div class="tasks">
                    <div v-for="item in list_task" :key="item.name" class="taskItem">
                        <input type="checkbox">
                        <h3>{{item.name}}</h3>
                    </div>
                </div>
                        
            </div>
            <div class="todoForm">
                <button @click="add" class="addTodo">+</button>
                <div class="form">
                    <label>Tâche: </label>
                    <input :value="taskeName"
                        placeholder="Rechercher une tâche"
                        @input="taskName = $event.target.value"
                    />
                    <select class="btn" id="priority">
                        <option value="urgent">Urgent</option>
                        <option value="important">Important</option>
                        <option value="not urgent">Not urgent</option>
                        <option value="not important">Not important</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoList",
    data(){
        return{
            list_task:[
                {
                    name: "Todo1"
                },
                {
                    name:"todo2"
                }
            ]
        }
    },
    methods: {
        add: function(){
            alert("test")
            this.list_task.push({name: "Hellow"})
            console.log(this.list_task)
        }
    }
};
</script>

<style>
.todo { 
    background-color: #bc8f8f;
    height: 800px;
    border-radius: 4%;
    padding-left: 50px;
    padding-right: 50px;
}

.title{
    padding-top: 30px;
    padding-bottom: 10px;
    text-align: center;
}
.container{
    width: 800px;
    display: flex;
    justify-content: center;
    align-content: space-between;
    width: 100%;
    height: 100%;
}

.todoList{
    width: 50%;
}

.todoForm{
    width: 30%;
    text-align: center;
    padding-left: 20px;
}

.searchBar input{
    margin-bottom: 50px;
    width: 440px;
}

.categories{
    display: flex;
    justify-content: space-between;
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
</style>