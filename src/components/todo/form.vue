<template>
    <div class="form">
        <button @click="close">X</button>
        <form @submit="addTask">


            <!-- LABEL -->
            <label>Tâche: </label>

            <!-- LABEL -->
            <label>{{text}}</label>


            <!-- NAME -->
            <input class="avenir" 
                placeholder="Ajouter une tâche"
                v-model="name"
                id="idTask"
                name="name"/>


            <!-- CATEGORY -->
            <select v-model="category" name="importance">
                <option disabled value="">Importance</option>
                <option value="urgent">Urgent</option>
                <option value="important">Important</option>
                <option value="pasimportant">Pas important</option>
            </select>
            

            <!--  CATEGORY -->
            <button type="submi">Ajouter</button> 
        

        </form>
    </div>
</template>

<script>
export default {
    name: "addTaskForm",
    props:{
        show: Boolean,
        text: String
    },
    data(){
        return{
            name:"",
            category: ""
        }
    },
    methods:{
        addTask(e){
            e.preventDefault()
            if(!this.name){
                alert('Ajouter une tâche!')
                return
            }

            const newTask={
                id: Math.floor(Math.random() * 10000),
                name: this.name,
                importance: this.importance
            }

            this.$emit('addTask', newTask)

            console.log(newTask)

            this.name = ''
            this.importance = ''
        }, 
        close(){
            this.$emit("update:show", false)
        }
    }
}
</script>
<style lang="scss" scoped>

.form{
    text-align: end;
    transition: all .7s ease-in-out;
    overflow: hidden;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100vw;
    display: flex;
    justify-content: end;
    background-color: rgb(171, 92, 61);

    &.true{
        height: 100px;
    }
    
    &.false{
        height: 0px;
    }
    form{
        padding-top: 5%;
        padding-bottom: 5%;
        padding-right: 2%;
    }
}



</style>