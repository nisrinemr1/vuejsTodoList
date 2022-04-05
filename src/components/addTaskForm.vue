<template>
    <div>
        <label>Tâche: </label>
        <input class="avenir" 
            placeholder="Rechercher une tâche"
        />
        <select v-model="selectedItem">
            <option v-for="item in items" :key="item" :value="item">{{item}}</option>
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
                    selectedItem: "important",
                    isHiddenForm: false, 
        }
    }
}
</script>

<style scoped>
</style>