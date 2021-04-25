<template lang="en">
    <header>
        <nav class="navbar navbar-inverse navbar-fixed-top" id="top">
            <div class="container-fluid">
                <div class="navbar-header" id="logo">
                    <h1 class="justify-content-left">Task Manager</h1>
                </div>
                <ul class="space"></ul>
                <ul></ul>
                <ul></ul>
                <ul class="nav navbar-nav navbar-right">
                    <li id="counter"><Count /></li>
                </ul>
            </div>
        </nav>
    </header>
</template>
<script>
import Count from './Count'
export default{
    name: 'Header',
    prop:{
        title:String,
    },
    components: {
        Count,
    },
}
</script>
<style scoped>
#top{
    background: none;
    -webkit-box-shadow: 0 8px 6px -18px whitesmoke;
       -moz-box-shadow: 0 8px 6px -18px whitesmoke;
            box-shadow: 0 8px 6px -8px whitesmoke;
}
#logo{
    margin-left: 0px;
    justify-content: left;

}
.space{
    width: 11px
}
#count{
    margin-right: 0px;
    justify-content: right;
}
</style>
