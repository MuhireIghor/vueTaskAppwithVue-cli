<template>
<header class='header'>
<h1>{{title}}</h1>
<Button @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask?'Close':'AddTask'" :color="showAddTask?'red':'green'"  />   
</header>
</template>
<script>
import Button from './Button'
export default{
    name:'Header',
    props:{
        title:{
            type:String,
            default:'Hello world'
        },
        showAddTask:Boolean,
    },
    components:{
        Button
    }
}
</script>
<style scoped>
.header{
    align-items:'center';
    justify-content:'space-between';
    display:'flex';
    margin-bottom:'20px';
}
</style>