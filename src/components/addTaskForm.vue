<template>
    <div>
        <form @submit="addTask">
            <label>Tâche: </label>
            <input class="avenir" 
                placeholder="Ajouter une tâche"
                v-model="name"
                id="idTask"
                name="name"/> 
            <select v-model="importance" name="importance">
                <option disabled value="">Importance</option>
                <option value="urgent">Urgent</option>
                <option value="important">Important</option>
                <option value="pasimportant">Pas important</option>
            </select>
            <br />
            <button type="submi">Ajouter</button>  <!-- v-bind:value="list_task.name + list_task.importance" -->
        </form>
    </div>
</template>

<script>
export default {
    name: "addTaskForm",
    props:{
        list_task: Array
    },
    data(){
        return{
            selected:"",
            name:"",
            importance:""
        }
    },
    methods:{
        addTask(e){
            e.preventDefault()
            if(!this.name){
                alert('Ajouter une tâche!')
                return
            }
            /* this.list_task.push.$emit({
                    id: this.nextTask++,
                    name: this.taskName,
                    importance: this.importance
            }) */
            const newTask={
                id: Math.floor(Math.random() * 10000),
                name: this.name,
                importance: this.importance
            }

            this.$emit('addTask', newTask)

            console.log(newTask)

            this.name = ''
            this.importance = ''
        }
    }
}
</script>
<style scoped>
</style>