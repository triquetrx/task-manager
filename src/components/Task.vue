<template>
    <div @click="expand(task.id)" :class="[task.reminder ? 'reminder':'task',task]" id="task">
        <h3 class="d-flex justify-content-start" id="text">{{ task.text }}</h3>            
        <div class="p" hidden><h4> Point:{{count}}</h4></div>
        <h5 class="d-flex justify-content-left" id="day">{{ task.day }}</h5>
        <br>
    </div>
</template>
<script>
import Button from './Button'
import Count from './Count'
export default {
    name:'Task',
    props:{
        task:Object
    },
    components:{
        Button,
        Count
    },
    methods: {
        expand(id){
            console.log(id)
        },
    },
}
</script>

<style scoped>
#task{
    color: white;
    margin:5px;
    padding: 10px 20px;
    cursor: pointer;
}
.reminder{
    border-left:2px solid whitesmoke;
}
#containerTask{
    margin: 10px;
}
h3,h5{
    width: fill;
    margin-left: 10px
}
.p{
    display:none,
}
.button:hover .p{
    display:block,
}
</style>