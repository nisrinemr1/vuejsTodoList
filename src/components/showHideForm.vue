<template>
    <div>
        <button @click="hide">+</button>
    </div>
</template>

<script>
export default {
    name: "showHideForm", 
    props:{
        hidden: Boolean,
        test: String,
        naruto: String
    },
    methods:{
        hide: function(){
            /* this.$emit("update:naruto", "I am sasuke :p") */
            /* if (this.hidden === true ){
                this.$emit("update:hidden", false)
            }
            else{
                this.$emit("update:hidden", true)
            } */
            this.$emit("update:hidden", !this.hidden)
        }
    }
}
</script>

<style scoped>

</style>