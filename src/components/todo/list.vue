<template>
    <div>
        <div class="searchBar">
            <input type="text" placeholder="Rechercher une tâche">
        </div>
        <div class="categories">
            <button class="btn">Urgent</button>
            <button class="btn">Important</button>
            <button class="btn">Pas important</button>
        </div>
        <div class="tasks">
            <div v-for="item in list_task" :key="item.name" class="taskItem">
                <!-- get the name from the list_task  -->
                <input class="avenir" type="checkbox">
                <h3>{{item.name}}</h3> <!-- to show up the item name -->
                <br />
                <p class="importance">{{item.importance}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TaskList",

    data(){ 
        return{
            list_task:[{
                id: 0,
                name: null,
                importance: null
            }]
        }
    },
    methods:{
        addTask(task){
            this.tasks = [...this.tasks, task]
        }
    }
}
</script>

<style scoped>
    .searchBar input{
    margin-bottom: 50px;
    width: 100%;
    }
    .categories{
        display: flex;
        justify-content: space-between;
    }
    .taskItem{
        border:1px solid pink;
        margin-bottom: 5%;
    }
    .importance{
        margin-left: 50%;
        margin-top: 6%;
    }
</style>