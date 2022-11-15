<template>
<div @dblclick = "$emit('toggle-Reminder',task.id)" :class="[task.reminder?'reminder':'']">
    <h3>{{task.text}}
    <p class="fas fas-times" @click="deleteTask(task.id)" > x</p>
    </h3>
    <h3>{{task.day}}</h3>
</div>
</template>
<script>
export default{
    name:"Task",
    props:{
        task:Object
    },
    methods:{
        deleteTask(id){
            this.$emit('delete-task',id);//for passing id to the upper component  with respcetive data about a task with a certain Id
            }
    },
    emits:[
        'toggle-Reminder','delete-task'
    ]
 
}

</script>
<style>
.reminder{
    border-left:4px solid green;
}
</style>