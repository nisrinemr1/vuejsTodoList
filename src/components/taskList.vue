<template>
    <div>
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
                <!-- get the name from the list_task  -->
                <input class="avenir" type="checkbox">
                <h3>{{item.name}}</h3> <!-- to show up the item name -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TaskList",
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
</style>