<template>
    <div class="todo">
        <h1 class="title">My TodoList</h1>
        <div class="todoList">
            <div class="listPart">
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
                        <input class="avenir" type="checkbox">
                        <h3>{{item.name}}</h3>
                    </div>
                </div>
                        
            </div>
            <div class="todoForm">
                <button v-on:click="isHiddenForm = !isHiddenForm">+</button>
            </div>
        </div>
        <div :class=" 'form ' + isHiddenForm ">
            <label>Tâche: </label>
            <input class="avenir" 
                :value="taskeName"
                placeholder="Rechercher une tâche"
                @input="taskName = $event.target.value"
            />
            <select v-model="selectedItem">
                <option v-for="item in items" :key="item" :value="item">{{item}}</option>
            </select>
            <br>
            <button class="btn">Ajouter</button>
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
            ],
            items: ['urgent', 'important', 'notImportant', 'notImportant'],
            selectedItem: "important",
            isHiddenForm: false,
        }
    },
    methods: {
        /* add: function(){
            this.list_task.push({name: "Hellow"})
            console.log(this.list_task)
        } */
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

.searchBar input{
    margin-bottom: 50px;
    width: 100%;
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