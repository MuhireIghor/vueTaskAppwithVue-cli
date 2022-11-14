<template>
<header class='header'>
<h1>{{title}}</h1>
<Button text='Add Task' color='green'  />   
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
        }
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