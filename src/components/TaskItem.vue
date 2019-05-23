<template>
    
    <div class="task-item" v-bind:class="{'is-done': task.done}" >
        <p>
            <input type="checkbox" v-on:change="markDone" :checked="task.done">
            {{task.title}}
            <button @click="$emit('del-task',task.id)"
             class="del">x</button>
        </p>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "TaskItem",
    props: ["task"],
    methods: {
        markDone(){
            if (this.task.done== false){
                axios.put(`http://localhost:3000/api/task/${this.task.id}/done`);
                console.log(this.task.title + ' ' + this.task.done)
            }else{
               axios.put(`http://localhost:3000/api/task/${this.task.id}/undone`);
                console.log(this.task.title + ' ' + this.task.done);
            }
            this.task.done = !this.task.done;
        }
    }
}

</script>

<style scoped >
 
    .task-item{
        background: #f4f4f4;
        padding : 10px;
        border-bottom: 1px #ccc dotted;
        width: 500px;
        margin: auto;
    }

    .is-done{
        text-decoration: line-through;
    }

    .del{
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 90%;
        cursor: pointer;
        float: right;
    }
</style> 