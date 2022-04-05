<template>

    <div class="todo">
        <div class="content">


            <!-- ************ TITLE ************-->
            <!-- ************ TITLE ************-->
            <!-- ************ TITLE ************-->
            <h1 class="title">My Todo</h1>


            <!-- ************ LIST ************-->
            <!-- ************ LIST ************-->
            <!-- ************ LIST ************-->
            <List/>


            <!-- ************ FORM ************-->
            <!-- ************ FORM ************-->
            <!-- ************ FORM ************-->
            <Form v-if="show_form" :show.sync="show_form" text="manga" @addTask="addTask"/>


            <!-- ************ SHOW FORM BUTTON ************-->
            <!-- ************ SHOW FORM BUTTON ************-->
            <!-- ************ SHOW FORM BUTTON ************-->
            <button v-else @click="show_form = true">+</button>




        </div>
    </div>

</template>

<script>

import Form from './todo/form.vue'
import List from './todo/list.vue'

export default {
    name: "Todo-Page",
    components: { 
        Form, 
        List
    },
    data(){
        return{
            show_form: false,
            manga: "naruto"
        }
    }
};
</script>

<style lang="scss">

    .todo { 
        background-color: #bc8f8f;
        height: 100vh;
        width: 100vw;
        display: flex;
        align-items: center;
        justify-content: center;
        .content{
            height: 90vh;
            width: 90vw;
        }
    }



 /* ********************* */
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