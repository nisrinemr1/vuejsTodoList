<template>
    <div>
        <label>Tâche: </label>
        <input class="avenir" 
            placeholder="Rechercher une tâche"
        />
        <select v-model="selectedItem"> <!-- pre define selection which is "important" in the data-->
            <option v-for="item in items" :key="item" :value="item">{{item}}</option>
            <!-- v-for is used to use elements from a tab. "Take the item in table items" :key is needed as well!-->
        </select>
        <br>
        <button class="btn">Ajouter</button>
    </div>
</template>

<script>
export default {
    name: "addTaskForm",
    data(){
        return{
            items: ['urgent', 'important', 'pas urgent', 'pas important'],
            selectedItem: "important" 
        }
    }
}
</script>
<style scoped>
</style>