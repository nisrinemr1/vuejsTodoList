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
            items: ['urgent', 'important', 'notImportant', 'notImportant'],
                    selectedItem: "important",
                    isHiddenForm: false, 
        }
    }
}
</script>

<style scoped>
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