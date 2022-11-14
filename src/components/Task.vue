<template>
<div >
    <h3>{{task.text}}</h3>
    <h3>{{task.day}}</h3>
</div>
</template>
<script>
export default{
    name:"Task",
    props:{
        task:Object
    }
}

</script>