<template>
    <form @submit="onSubmit" class="form-looks">
        <div class="form-group">
            <div class="taskname">
                <label for="taskName">Task Name</label>
                <input type="task_name" v-model="text" class="form-control" id="taskName" placeholder="Task ToDo"/>
            </div>
        </div>
        <div class="form-group">
            <label for="dateTime">Day & Time</label>
            <input type="date_Time" v-model="day" class="form-control" id="dateTime" placeholder="Add Day & Time"/>
        </div>
        <div class="form-group">
            <label for="priorityForm">Priority</label>
            <select class="form-control" v-model="priority" id="priorityForm">
                <option>High</option>
                <option>Medium</option>
                <option>Low</option>
            </select>
        </div>
        <div class="d-flex justify-content-center" id="buttons">

            <button type="submit" class="p-3 bd-highlight" id='taskSubmit'>Add Task</button>
            <button @click= "closeAll()" type="clear" class="p-3 bd-highlight" id='clear'>Changed My Mind</button>
        </div>
    </form>

</template>

<script>
export default {
    name:'AddTask',
    data(){
        return{
            text:'',
            day:'',
            priority:'',
            reminder:false,
        }
    },
    methods: {
        onSubmit(e){
            e.preventDefault()
            if(!this.text){
                alert('Please Add a Task Name')
                return
            }
            if(!this.day){
                alert('Please Enter the dateTime')
            }
            const newTask={
                id:Math.floor(Math.random()),
                text: this.text,
                day: this.day,
                priority:this.priority,
                reminder: this.reminder
            }
            this.$emit('add-Task',newTask)
            this.text='',
            this.day='',
            this.priority='',
            this.reminder=false
        },
        closeAll(){
            this.$emit('closeAll')
        },
    },
}
</script>

<style scoped>
form{
    margin: 40px;
    color: whitesmoke;
    font-weight: bolder;
    font-size: medium;
}
option{
    color: #181818;
}
.taskname{
    display: inline;
}

button{
    align-content: center;
    background: #9E2B25;
    border: #9E2B25;
    padding: 10px 32px;
    border-radius: 10px;
    margin:10px
}
#clear{
    background: whitesmoke;
    color: black;
}

button:hover{
    background: #9E2B25;
    border: #9E2B25;
    box-shadow: 1px 1px 10px whitesmoke;
}
</style>