<template lang="en">
    <button @click="onClick()" :style="{ background:color }" class="box">{{text}}</button>
</template>
<script>
export default{
    name:'Button',
    props: {
        text:String,
        color:String
    },
    methods: {
        onClick(){
            this.$emit('add-new-task')
            this.$emit('clear-task')
        },
    },
}
</script>

