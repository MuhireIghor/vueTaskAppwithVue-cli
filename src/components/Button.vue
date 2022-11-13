<template>
<button class='btn':style="{background:color}" @click='onClick()'>{{text }}</button>
</template>
<sript>
export default {
    name:'Button',
    props:{
        text:String,
        color:String
    },
    methods:{
        onClick(){
            console.log("clicked")
        }
    }
}
</sript>