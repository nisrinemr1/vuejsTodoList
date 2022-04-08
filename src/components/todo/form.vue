<template>
    <div class="form">

        <!-- CLOSE FORM BUTTON -->
        <button class="close-form-btn" @click="close">X</button>


        <form @submit="addTask">


            <!-- LABEL -->
            <label>Tâche: </label>


            <!-- NAME -->
            <input class="avenir" 
                placeholder="Ajouter une tâche"
                v-model="name"
                id="idTask"
                name="name"/>


            <!-- CATEGORY -->
            <select v-model="category" name="importance">
                <option disabled>Importance</option>
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
        show: Boolean
    },
    data(){
        return{
            name: "",
            category:""
        }
    },
    methods:{
        addTask(e){
            e.preventDefault()
            const newTask={
                id: Math.floor(Math.random() * 10000),
                name: this.name,
                category: this.category,
                isdone: false
            }

            this.$emit('uptdate:id', this.id)
            this.$emit('uptdate:name', this.name )
            this.$emit('uptdate:category', this.category )
            this.$emit('uptdate:isdone', this.isdone )

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
    overflow: hidden;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100vw;
    display: flex;
    justify-content: end;
    flex-direction: row-reverse;
    background-color: white;
    padding-top: 20px;
    padding-bottom: 30px;

    .close-form-btn{
        margin-bottom: 60px;
        margin-right: 40px;
        border: none;
        font-size: 1.1rem;
        background-color: white;
    }
    
    form{
        padding-top: 40px;

        label{
            padding-right: 15px;
        }

        input{
            margin-right: 15px;
            border-radius: 20px;
            background-color: rgb(253, 197, 207);
            border: none;
            padding-top: 5px;
            padding-bottom: 5px;
            padding-left: 15px;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
        }

        select{
            margin-right: 15px;
            padding-top: 5px;
            padding-bottom: 5px;
            padding-left: 5px;
            padding-right: 5px;
            background-color: rgb(253, 197, 207);
            border: none;
            border-radius: 20px;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
        }

        button{
            padding-top: 10px;
            padding-bottom: 10px;
            padding-left: 10px;
            padding-right: 10px;
            background-color: rgb(253, 197, 207);
            border: none;
            border-radius: 20px;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
        }

        button:hover{
            background-color: rgb(254, 212, 220);
        }

    }
}



</style>