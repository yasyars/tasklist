<template>
<div>
    <form @submit="addTask">
        <input type="text" v-model="title" name="title" placeholder="Add task..."> 
        <input type="submit" value="Submit" class="btn">
    </form>
</div>
</template>

<script>
// import uuid from 'uuid';

export default{
    name: "AddTask",
    data(){
        return{
            title:''
        }
    },
    methods: {
        addTask(e){
            e.preventDefault();    
            const newTask={
                title: this.title,
                done : false
            }
            //send to parent
            this.$emit('add-task', newTask );

            this.title= '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        height: 60px;
        padding : 10px;
        border-bottom: 1px #ccc dotted;
        width: 500px;
        margin: auto;

        
    }

    input[type="text"]{
        flex:10;
        padding:5px;
        margin-right: 5px;
        font-size:10pt;

    }

    input[type="submit"]{
        flex:2;
        font-size:10pt;
    }
</style>