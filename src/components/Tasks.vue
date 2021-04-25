<template>
    <div class="task-main" :key="task.id" v-for="task in tasks" id="tasksToDo" >
        <!--<h2>{{ task.text }}</h2>-->
        <div class="d-flex justify-content,task_priority"  id="outerBorder" :class="task_priority">
            <div class="p-2 flex-fill bd-highlight">
                <Task class="mr-auto p-2" :task="task" />
            </div>
            <div class="btn">
                <div class="p-2">
                    <button @click="$emit('toggle-reminder',task.id)" class="" id="reminderbtn">
                        <i class="fas fa-bell" style="color:black"></i>
                    </button>
                    <button @click="$emit('view-more',task.id)" class="" id="viewMore">
                        <i class="fas fa-check"></i>
                    </button>
                    <button @click="$emit('increase-id',task.priority)" class="" id="priority">
                        <i class="fas fa-arrows-alt-v"></i>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Task from './Task'
export default {
    name:'Tasks',
    props:{
        tasks: Array
    },
    components: {
        Task,
    },
    emit:['view-more', 'toggle-reminder'],
}
</script>
<style scoped>
#outerBorder{
    background:rgba(255, 255, 255, 0.05);
    padding-left: 10px;
    padding-right: 10px;
    margin:5px
}
.btn{
    margin-right: 3px;
    height: 45px;
}
.task_priority.high {color: red}
.task_priority.medium {color: yellow}
.task_priority.low {color: green}
#tasksToDo{
    background: rgba(10, 10, 10, 0.212);
}
#viewMore{
    font-weight: bold;
    display: inline-block;
    background: #009B72;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
    transition: 0.5s;
}
#viewMore:hover{
    box-shadow: 1px 1px 10px whitesmoke;
    transition-duration: ease-in;
}
#reminderbtn{
    font-weight: bold;
    display: inline-block;
    background: whitesmoke;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
    transition: 0.5s;
}
#priority{
    font-weight: bold;
    display: inline-block;
    background: #9E2B25;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
    transition: 0.5s;
}
#priority:hover{
    box-shadow: 1px 1px 10px whitesmoke;
    transition-duration: ease-in;
}
#reminderbtn:hover{
    box-shadow: 1px 1px 10px whitesmoke;
    transition-duration: ease-in;
}
</style>